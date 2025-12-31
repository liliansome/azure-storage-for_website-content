# azure-storage-for_website-content
Azure Blob Storage for Public Website Content
# Azure Blob Storage for Public Website Content

[![Azure Storage](https://img.shields.io/badge/Azure-Storage-blue)](https://azure.microsoft.com/en-us/services/storage/blobs/)
[![Geo-Redundant](https://img.shields.io/badge/Geo--Redundant-RA-GRS-green)](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy)
[![CDN Ready](https://img.shields.io/badge/CDN-Ready-orange)](https://azure.microsoft.com/en-us/services/cdn/)
[![Soft Delete](https://img.shields.io/badge/Soft%20Delete-21%20Days-yellow)](https://docs.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-overview)

##  Business Context
**Global Company Website** serving product images, videos, marketing literature, and customer success stories to worldwide customers. Mission-critical content requiring low latency load times and high availability.

##  Requirements
- **High Availability**: Survive regional outages
- **Low Latency**: Fast global access to content
- **Version Control**: Track document revisions
- **Disaster Recovery**: Restore deleted/modified files
- **Public Access**: Anonymous read access for customers
- **Scalability**: Handle rapid demand expansion

##  Architecture Diagram

```mermaid
graph TB
    subgraph "Azure Storage Account"
        A[Blob Container: public]
        B[Redundancy: RA-GRS]
        C[Soft Delete: 21 days]
        D[Versioning: Enabled]
        E[Public Access: Blob-level]
    end
    
    subgraph "Global Customers"
        F[Customer US]
        G[Customer EU]
        H[Customer APAC]
    end
    
    subgraph "Content Types"
        I[Product Images]
        J[Marketing Videos]
        K[Success Stories]
        L[Documents]
    end
    
    I --> A
    J --> A
    K --> A
    L --> A
    
    A -- Read Replicas --> B
    
    F -- Low Latency --> A
    G -- Low Latency --> A
    H -- Low Latency --> A
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
