# Plugin Documentation: `donation-engine`

The `donation-engine` is the core financial hub of the platform. It handles the entire lifecycle of a donation—from the moment a donor selects a campaign to the final delivery of a tax-compliant receipt.

---

## 💎 The Detailed Donation Flow

The system implements a multi-stage process designed for high security and a Frictionless donor experience.

### Phase 1: Intent & Localization
1.  **Campaign Selection**: The donor selects a specific campaign (e.g., Zakat, General Fund, Sadqah) from the frontend.
2.  **Currency Detection**: The system identifies the user's regional context to provide appropriate currency options and localized formatting.

### Phase 2: Stateful Cart Management
The system implements a proprietary **multi-item basket system**:
*   **Session Persistence**: Donations are stored in a secure server-side session, allowing donors to add multiple causes to a single transaction.
*   **Asynchronous (AJAX) Interaction**: The cart is managed via custom WordPress AJAX handlers, ensuring the UI remains responsive without page reloads.
*   **Real-Time Recalculation**: Every modification triggers an immediate recalculation of the grand total and currency symbols.

### Phase 3: Data Enrichment & Validation
1.  **Address Standardization (Geocoding)**:
    *   The system communicates with a **Standardization Service** to format the address correctly using external API intelligence.
    *   Detailed components (City, Postal Code, Country) are extracted for accurate financial reporting.
2.  **Integrity Checks**: The engine validates donor data to ensure formatting and completeness before initiating the payment sequence.

### Phase 4: Secure Payment Processing
1.  **PCI-Compliant Tokenization**: The system uses a secure, client-side bridge to tokenized sensitive payment info. No credit card data ever touches the local server.
2.  **Transaction Execution**: The backend processes the tokenized transaction through a secure gateway.
3.  **Webhook Fulfillment**: Upon successful payment, the gateway sends a secure signal back to the server to trigger fulfillment actions.

### Phase 5: Automated Fulfillment & Notifications
1.  **Dynamic PDF Generation**: The system parses the transaction data and generates a professional, tax-compliant receipt PDF on-the-fly using the **Dompdf** engine.
2.  **Intelligent Notification Routing**:
    *   The system identifies the donor's selected regional context.
    *   The receipt is emailed to the donor immediately.
    *   Detailed notifications with the PDF attachment are routed to specific administrative authorities based on the campaign type and region.

---

## Key Technical Modules

### 1. Dynamic PDF Engine
*   **HTML-to-PDF Conversion**: Transforms complex submission data into professionally formatted A4 PDF documents.
*   **Base64 Asset Embedding**: Branding elements are embedded to ensure perfect rendering across all environments.
*   **Automated Storage**: Saves generated PDFs to a secure, non-indexed directory for archival.

### 2. Intelligent Notification System
*   **Regional Logic**: Dynamically identifies notification lists based on the selected campaign region.
*   **Role-Based Distribution**: Ensures that different administrative stakeholders receive appropriate levels of data.

### 3. Custom Backend Infrastructure
*   **Secure AJAX Handlers**: Dedicated routes for cart manipulation and data validation.
*   **Enhanced Connectivity**: Optimizes HTTP request handling for reliable communication with external financial services.

## Security & Compliance
*   **No PII Leakage**: Sensitive donor data is handled via secure hooks and never exposed in client-side logs.
*   **Permission Callbacks**: All administrative and data routes are protected by strict capability mapping.
*   **Audit Logging**: Every stage of the donation flow is logged for internal reconciliation and security auditing.
