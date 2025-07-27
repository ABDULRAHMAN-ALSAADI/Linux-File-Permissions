```mermaid
flowchart TD
    %% Styling with larger elements
    classDef headerBox fill:#2563eb,stroke:#1d4ed8,stroke-width:3px,color:#ffffff,font-weight:bold,font-size:16px
    classDef conceptBox fill:#10b981,stroke:#059669,stroke-width:3px,color:#ffffff,font-weight:bold,font-size:14px
    classDef detailBox fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#ffffff,font-size:13px
    classDef commandBox fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#ffffff,font-size:13px
    classDef exampleBox fill:#ef4444,stroke:#dc2626,stroke-width:2px,color:#ffffff,font-size:13px
    
    %% MAIN HEADER
    A["🐧 LINUX FILE PERMISSIONS<br/>Basic Guide"]:::headerBox
    
    %% PERMISSION TYPES
    A --> B["📋 PERMISSION TYPES"]:::conceptBox
    
    B --> B1["📖 Read (r) = 4<br/>View file content"]:::detailBox
    B --> B2["✏️ Write (w) = 2<br/>Modify file content"]:::detailBox
    B --> B3["⚡ Execute (x) = 1<br/>Run file/enter directory"]:::detailBox
    
    %% USER CATEGORIES
    B1 --> C["👥 USER CATEGORIES"]:::conceptBox
    B2 --> C
    B3 --> C
    
    C --> C1["👤 Owner (u)<br/>File creator"]:::detailBox
    C --> C2["👥 Group (g)<br/>Assigned group"]:::detailBox
    C --> C3["🌍 Others (o)<br/>Everyone else"]:::detailBox
    
    %% VIEWING PERMISSIONS
    C1 --> D["👀 VIEW PERMISSIONS"]:::conceptBox
    C2 --> D
    C3 --> D
    
    D --> D1["📋 ls -l filename<br/>Output: -rwxr-xr-x"]:::commandBox
    
    %% PERMISSION CALCULATION
    D1 --> E["🧮 CALCULATE PERMISSIONS"]:::conceptBox
    
    E --> E1["rwx = 4+2+1 = 7<br/>rw- = 4+2+0 = 6<br/>r-x = 4+0+1 = 5<br/>r-- = 4+0+0 = 4"]:::detailBox
    
    %% CHANGING PERMISSIONS
    E1 --> F["🔧 CHANGE PERMISSIONS"]:::conceptBox
    
    F --> F1["📝 Symbolic Method<br/>chmod u+x file<br/>chmod g-w file<br/>chmod o=r file"]:::commandBox
    
    F --> F2["🔢 Octal Method<br/>chmod 755 file<br/>chmod 644 file<br/>chmod 600 file"]:::commandBox
    
    %% COMMON EXAMPLES
    F1 --> G["🎯 COMMON PERMISSIONS"]:::conceptBox
    F2 --> G
    
    G --> G1["755 (rwxr-xr-x)<br/>📁 Directories & Scripts"]:::exampleBox
    G --> G2["644 (rw-r--r--)<br/>📄 Regular Files"]:::exampleBox
    G --> G3["600 (rw-------)<br/>🔒 Private Files"]:::exampleBox
    
    %% OWNERSHIP
    G1 --> H["👑 CHANGE OWNERSHIP"]:::conceptBox
    G2 --> H
    G3 --> H
    
    H --> H1["chown user:group file<br/>chgrp group file"]:::commandBox
