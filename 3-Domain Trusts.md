## **Domain Trusts**

Trust Direction
- One-way trust – Unidirectional. Users in the trusted domain can access resources in the trusting domain but the reverse is not true
- Two-way trust – Bi-directional. Users of both domains can access resources in the other domain.

Default/AutomaticTrusts
– Parent-child trust – It is created automatically between the new domain and the domain that precedes it in the namespace hierarchy, whenever a new domain is added in a tree. For example, dollarcorp.moneycorp.local is a child of moneycorp.local
– This trust is always two-way transitive.

Domain Trust mapping
Get a list of all domain trusts for the current domain Get-NetDomainTrust
- Get-NetDomainTrust –Domain us.dollarcorp.moneycorp.local

AD Module
- Get-ADTrust
- Get-ADTrust –Identity us.dollarcorp.moneycorp.local

Forest mapping
- Get details about the current forest
- Get-NetForest
- Get-NetForest –Forest eurocorp.local Get-ADForest
AD moudule
- Get-ADForest –Identity eurocorp.local

Get all domains in the current forest Get-NetForestDomain
- Get-NetForestDomain –Forest eurocorp.local
AD module
- (Get-ADForest).Domains

Forest mapping
Get all global catalogs for the current forest
- Get-NetForestCatalog
- Get-NetForestCatalog –Forest eurocorp.local
AD Module
- Get-ADForest | select -ExpandProperty GlobalCatalogs

Map trusts of a forest
- Get-NetForestTrust
- Get-NetForestTrust –Forest eurocorp.local
AD Module
- Get-ADTrust -Filter 'msDS-TrustForestTrustInfo -ne "$null"'
