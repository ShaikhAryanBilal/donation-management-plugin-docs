# Theme Documentation: `portal-theme`

The `portal-theme` is a custom-built WordPress theme designed for an enterprise-level donation platform. It serves as the primary interface for donors and administrators, prioritizing performance, accessibility, and clean aesthetics.

## Core Features

### 1. Donor Dashboard
*   **Transaction History**: A bespoke interface (`page-donor-dashboard.php`) that allows donors to view their historical contributions and manage recurring donations.
*   **Receipt Management**: Secure access to download tax-compliant PDFs of all past donations.
*   **Regional Selection**: A dynamic UI for donors to select specific regional causes or global funds.

### 2. Specialized Page Templates
The theme includes specialized layouts for diverse fundraising needs:
*   `page-donate.php`: A streamlined, conversion-focused layout for quick donations.
*   `single-campaign.php`: A deep-dive layout for specific high-impact initiatives.
*   `page-annualreports.php`: A layout focused on financial transparency and document sharing.
*   `page-thankyou.php`: A personalized post-donation experience with automated summary data.

### 3. Technical Implementation
*   **Modern Frontend Stack**: Built using **Bootstrap 5**, **Slick Carousel**, and **FontAwesome 6**.
*   **Modular Architecture**: Extensively uses WordPress template parts to maintain a scalable codebase.
*   **Real-time UI Updates**: Integrated with custom AJAX handlers to update cart totals and currency symbols instantly.
*   **Asset Optimization**: Versioned CSS/JS enqueuing to ensure performance and prevent caching issues.

## Design Philosophy
*   **Trust-Building Visuals**: High-contrast typography and clean spacing to ensure professional branding.
*   **Responsive Integrity**: A mobile-first approach ensuring that the donation flow is Frictionless on smartphones and tablets.
*   **Global Accessibility**: Optimized for low-bandwidth regions while maintaining a premium, modern aesthetic.

## Developer Notes
*   **Field Management**: Heavily relies on custom meta fields for flexible campaign management.
*   **Clean Transitions**: Subtle micro-interactions to guide the donor through the multi-step giving process.
