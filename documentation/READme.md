# Day 3 - API Integration and Data Migration Report
**Marketplace Name:** [WOODEN ASPIRE]

## Objective

The goal of Day 3 was to integrate APIs and migrate data into Sanity CMS to build a functional marketplace backend. This involved understanding API integration, migrating data from various sources, and ensuring compatibility with the Sanity schema. The day also focused on replicating real-world practices, such as integrating headless APIs and migrating data from popular eCommerce platforms.

## Key Learning Outcomes

*   **API Integration in Next.js:** Learned how to integrate APIs into a Next.js project.
*   **Data Migration to Sanity CMS:** Explored methods to migrate data from APIs into Sanity CMS.
*   **Handling eCommerce Data:** Gained experience working with data from platforms like Shopify, WooCommerce, and custom APIs.
*   **Schema Validation:** Developed skills to validate and adjust schemas to align with data sources.

## Steps Taken

### 1. Understanding the Provided API

*   **API Documentation Review:**
    *   Reviewed the API documentation for the assigned template.
    *   Identified key endpoints, including:
        *   Product listings (`/products`)
        *   Categories (`/categories`)
        *   Order history (`/orders`) (if applicable)
*   **API Testing:**
    *   Used Postman to test the API endpoints and verify the structure of the returned data.
    *   Gained understanding of data fields and their types.

### 2. Validating and Adjusting the Schema

*   **Schema Comparison:**
    *   Compared the existing Sanity CMS schema (created on Day 2) with the API data structure.
    *   Example:
        *   API Field: `product_title`
        *   Schema Field: `name`
*   **Schema Adjustments:**
    *   Adjusted the Sanity schema to ensure compatibility with the API data.
    *   Included renaming fields, changing data types, and establishing relationships between documents.

### 3. Data Migration

Explored three methods for data migration:

#### a. Using the Provided API

*   **Script Development:**
    *   Wrote a script to fetch data from the API, transform it to match the Sanity schema, and upload it to Sanity CMS.
*   **Tools Used:** Node.js, Axios, and Sanity Client.
*   **Example Code Snippet:**

```javascript
const sanityClient = require('@sanity/client');
const axios = require('axios');

const client = sanityClient({
  projectId: 'your-project-id',
  dataset: 'production',
  token: 'your-sanity-token',
  useCdn: false,
});

async function fetchAndMigrateData() {
  const response = await axios.get('[https://api.example.com/products](https://api.example.com/products)');
  const products = response.data;

  products.forEach(async (product) => {
    await client.create({
      _type: 'product',
      name: product.product_title,
      description: product.description,
      price: product.price,
    });
  });
}

fetchAndMigrateData();
```

#### b. Manual Import

*   **Exporting Data:**
    *   For smaller datasets, exported data from the API as JSON.
    *   Used Sanity’s built-in import tool to upload the data.
*   **Steps:**
    1.  Exported data as JSON.
    2.  Used Sanity’s import tool to upload the file.
    3.  Verified the imported data in the Sanity dashboard.

#### c. Using External Platform APIs

*   **Fetching Data:**
    *   Fetched data from an external platform (e.g., Shopify) and mapped the fields to the Sanity schema.
*   **Example:**
    *   Shopify Field: `title` → Sanity Field: `name`
    *   Shopify Field: `body_html` → Sanity Field: `description`

### 4. API Integration in Next.js

*   **Utility Functions:**
    *   Created utility functions to fetch data from the API and Sanity CMS.
*   **Example Code Snippet:**

```javascript
export async function getProducts() {
  const response = await fetch('[https://api.example.com/products](https://api.example.com/products)');
  const data = await response.json();
  return data;
}
```

*   **Rendering Data in Components:**
    *   Integrated the API data into the frontend by rendering product listings and categories in React components.
*   **Example Component:**

```javascript
export default function ProductList({ products }) {
  return (
    <div>
      {products.map((product) => (
        <div key={product.id}>
          <h2>{product.name}</h2>
          <p>{product.description}</p>
          <p>${product.price}</p>
        </div>
      ))}
    </div>
  );
}
```

*   **Testing API Integration:**
    *   Tested the API integration using Postman and browser developer tools.
    *   Added error handling to manage failed requests gracefully.

## Expected Output

*   **Sanity CMS:**
    *   Successfully populated with data from the provided API and external sources.
    *   Verified data alignment with the schema.
*   **Next.js Frontend:**
    *   Functional API integration displaying:
        *   Product listings.
        *   Categories.
        *   Other relevant data.

## Best Practices Followed

*   **Security:**
    *   Used `.env` files to store sensitive data like API keys.
*   **Clean Coding:**
    *   Used descriptive variable names and modularized functions.
    *   Added comments to explain complex logic.
*   **Validation:**
    *   Validated data during migration using schemas.
    *   Logged discrepancies for further investigation.
*   **Documentation:**
    *   Documented every step with screenshots, scripts, and testing notes.
    *   Maintained a changelog for schema adjustments.
*   **Version Control:**
    *   Committed changes frequently with meaningful messages.
    *   Tagged significant milestones in the repository.
*   **Testing:**
    *   Tested API integration thoroughly using Postman and browser tools.
    *   Handled edge cases like empty responses and invalid data.
*   **Peer Review:**
    *   Shared code and documentation with peers for feedback.
    *   Incorporated suggestions to improve quality.

## Conclusion

Day 3 was a comprehensive learning experience in API integration and data migration. By following the steps and best practices, I successfully integrated APIs into my Next.js project, migrated data into Sanity CMS, and ensured compatibility with my schema. This hands-on exercise has prepared me to handle real-world scenarios involving diverse data sources and client requirements.
```

