# Salesforce → ActiveCampaign Donation Integration

## Overview

This project provides a **one-directional API integration between Salesforce and ActiveCampaign** for transferring donation data.

The integration retrieves donation information from **Salesforce** and sends it to **ActiveCampaign**, where the donation data is stored as **Custom Objects associated with an ActiveCampaign contact**.

### Data Flow

```text
Salesforce
    │
    │  Donation Data
    ▼
API Integration
    │
    │  API Request
    ▼
ActiveCampaign
    │
    ▼
Contact → Donation Custom Object
```

The integration is **one-directional**:

**Salesforce → ActiveCampaign**

No data is sent from ActiveCampaign back to Salesforce.

## Purpose

The purpose of this integration is to make Salesforce donation information available within ActiveCampaign so that donation history can be associated with individual contacts.

This allows ActiveCampaign to use donation information for:

* Contact and donor history
* Marketing automation
* Donor segmentation
* Personalized communications
* Campaign workflows
* Reporting and other contact-related processes

## Integration Components

### Salesforce

Salesforce serves as the **source system** for donation data.

The integration retrieves relevant donation information from Salesforce and prepares the data for transfer to ActiveCampaign.

### API Integration

The integration acts as the intermediary between Salesforce and ActiveCampaign.

It is responsible for:

1. Connecting to Salesforce
2. Retrieving donation data
3. Identifying the corresponding ActiveCampaign contact
4. Formatting the donation data
5. Sending the data to ActiveCampaign through the ActiveCampaign API
6. Creating or updating the appropriate donation Custom Object associated with the contact

### ActiveCampaign

ActiveCampaign serves as the **destination system**.

Donation information is stored as a **Custom Object** associated with an ActiveCampaign contact.

This allows each contact to have one or more donation records associated with their contact record.

## Data Relationship

The basic relationship between the systems is:

```text
Salesforce Donation
        │
        ▼
ActiveCampaign Contact
        │
        ├── Donation Custom Object
        ├── Donation Custom Object
        └── Donation Custom Object
```

Multiple donation records can be associated with a single ActiveCampaign contact, allowing a contact's donation history to be maintained within ActiveCampaign.

## Direction of Data

| Source     | Destination    | Data          |
| ---------- | -------------- | ------------- |
| Salesforce | ActiveCampaign | Donation Data |

This project does **not** provide a reverse integration from ActiveCampaign to Salesforce.

## API Authentication

The integration uses API authentication to communicate with Salesforce and ActiveCampaign.

Authentication credentials and other sensitive configuration values should be stored securely and **must not be committed to the GitHub repository**.

Environment variables or another secure configuration method should be used for credentials such as:

* Salesforce API credentials
* ActiveCampaign API credentials
* API URLs
* Other environment-specific configuration

## Security

Do not commit API keys, access tokens, passwords, client secrets, or other sensitive credentials to the repository.

Use environment variables or a secure secrets-management solution for sensitive configuration.

## Project Architecture

At a high level, the integration follows this process:

1. **Retrieve donation data from Salesforce**
2. **Process and transform the data**
3. **Locate the corresponding ActiveCampaign contact**
4. **Create or update the donation Custom Object**
5. **Associate the Custom Object with the ActiveCampaign contact**

## Technologies

The project uses API-based communication between:

* **Salesforce API**
* **ActiveCampaign API**

Additional technologies and dependencies are documented within the project source code and configuration files.

## Important Notes

* Salesforce is the **source of truth** for donation data.
* ActiveCampaign is the **destination** for donation data.
* The integration is **one-directional**.
* Donation records are stored in ActiveCampaign as **Custom Objects** associated with contacts.
* Changes made to donation data in ActiveCampaign are not synchronized back to Salesforce.
* API credentials should never be stored directly in source code.

## License

This project is proprietary unless otherwise specified.
