# WoodenAspire Marketplace - Deployment and Staging

This document outlines the deployment process and staging environment setup for the WoodenAspire marketplace, detailing the steps taken on Day 6 of development.  This process ensures a smooth transition to production and a robust, real-world-ready platform.

## Table of Contents

* [Objective](#objective)
* [Key Learning Outcomes](#key-learning-outcomes)
* [Staging Environment Setup](#staging-environment-setup)
    * [Hosting Platform Setup](#hosting-platform-setup)
    * [Configuring Environment Variables](#configuring-environment-variables)
    * [Deploying to Staging](#deploying-to-staging)
* [Staging Environment Testing](#staging-environment-testing)
    * [Testing Types](#testing-types)
    * [Test Case Report](#test-case-report)
    * [Performance Testing](#performance-testing)
* [Project Organization](#project-organization)
* [Deployment Documentation](#deployment-documentation)
* [Next Steps](#next-steps) (Optional)


## Objective

The primary objective of Day 6 was to prepare the WoodenAspire marketplace for deployment by setting up a staging environment, configuring hosting, and ensuring the application is customer-ready. This involved building upon the testing and optimization efforts from Day 5 to guarantee smooth operation in a production-like setup.  We also established a clear understanding of managing different environments (TRN, DEV, SIT, UAT, PROD, DR).

## Key Learning Outcomes

* Set up and configure a staging environment using Vercel.
* Implement professional environment management practices.
* Perform thorough testing in the staging environment.
* Prepare professional deployment documentation.
* Organize project files and documents in a structured GitHub repository.

## Staging Environment Setup

### Hosting Platform Setup

* **Platform Choice:** Vercel was selected for its ease of use with Next.js applications and quick deployment capabilities.  Alternatives like Netlify, AWS, and Azure were considered.
* **Repository Connection:** The GitHub repository was linked to Vercel.
* **Build Settings:**
    * Build Command: `npm run build`
    * Output Directory: `.next`
* **Deployment Scripts:** Deployment scripts were verified in `package.json`.

### Configuring Environment Variables

* **Local `.env` File:** A `.env` file was created locally to store sensitive information:
    ```
    NEXT_PUBLIC_SANITY_PROJECT_ID=your_project_id
    NEXT_PUBLIC_SANITY_DATASET=production
    API_KEY=your_api_key
    ```
    This file was added to `.gitignore`.
* **Vercel Environment Variables:** The same environment variables were added to the Vercel dashboard under Environment Settings.

### Deploying to Staging

* **Deployment Trigger:** The initial deployment to the Vercel staging environment was triggered.
* **Deployment Validation:** After a successful build, the staging URL was accessed and validated:
    * Navigation between pages was verified.
    * API calls were tested.
    * Layout rendering was checked.

## Staging Environment Testing

### Testing Types

* **Functional Testing:** Features like product listing, search, and cart operations were tested.
* **Performance Testing:** Lighthouse was used to measure speed, responsiveness, and overall performance.
* **Security Testing:** API communication security and input validation were checked.

### Test Case Report

_(Detailed test case reports should be included here, either directly or linked as separate documents in the `documents/` folder.)_  This section should include specific test cases, expected results, and actual results.

### Performance Testing

_(Detailed performance test results, including Lighthouse scores and specific metrics, should be included here.)_  This could include screenshots or links to reports.

## Project Organization

The project files are organized in the following structure:

```
src/        - Main application source code
public/     - Static assets
documents/ - Reports, test cases, deployment documentation
README.md  - Project summary and documentation (this file)
```

## Deployment Documentation

This `README.md` file serves as the primary deployment documentation.  Further details, such as specific configurations and troubleshooting steps, can be added to the `documents/` folder.

## Next Steps (Optional)

* Implement continuous integration/continuous deployment (CI/CD) pipelines.
* Set up monitoring and logging for the production environment.
* Document any known issues or limitations.
* Prepare for User Acceptance Testing (UAT).

This structured approach to deployment and documentation ensures a maintainable and scalable platform for the WoodenAspire marketplace.
