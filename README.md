flowchart TB
    %% Styling
    classDef headerBox fill:#2563eb,stroke:#1d4ed8,stroke-width:2px,color:#ffffff,font-weight:bold
    classDef conceptBox fill:#10b981,stroke:#059669,stroke-width:2px,color:#ffffff,font-weight:bold
    classDef detailBox fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#ffffff
    classDef commandBox fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#ffffff
    classDef exampleBox fill:#ef4444,stroke:#dc2626,stroke-width:2px,color:#ffffff
    
    %% Main Header
    A[🐧 Linux File Permissions]:::headerBox
    
    %% Three Main Concepts
    A --> B[📋 Permission Types]:::conceptBox
    A --> C[👥 User Categories]:::conceptBox  
    A --> D[🔢 Representations]:::conceptBox
    
    %% Permission Types Branch
    B --> B1["📖 Read (r) = 4<br/>View file content"]:::detailBox
    B --> B2["✏️ Write (w) = 2<br/>Modify file content"]:::detailBox
    B --> B3["⚡ Execute (x) = 1<br/>Run file/enter dir"]:::detailBox
    
    %% User Categories Branch
    C --> C1["👤 Owner (u)<br/>File creator"]:::detailBox
    C --> C2["👥 Group (g)<br/>Assigned group"]:::detailBox
    C --> C3["🌍 Others (o)<br/>Everyone else"]:::detailBox
    
    %% Representations Branch
    D --> D1["📝 Symbolic<br/>rwxr-xr-x"]:::detailBox
    D --> D2["🔢 Octal<br/>755"]:::detailBox
    
    %% Commands Section
    E[⚙️ Commands & Operations]:::headerBox
    
    E --> F["👀 View Permissions<br/>ls -l filename"]:::commandBox
    E --> G["🔧 Change Permissions<br/>chmod"]:::commandBox
    E --> H["👑 Change Ownership<br/>chown user:group file"]:::commandBox
    
    %% Chmod Examples
    G --> G1["📝 Symbolic Method<br/>chmod u+x file<br/>chmod g-w file<br/>chmod o=r file"]:::exampleBox
    G --> G2["🔢 Octal Method<br/>chmod 755 file<br/>chmod 644 file<br/>chmod 600 file"]:::exampleBox
    
    %% Common Permission Sets
    I[🎯 Common Permission Sets]:::headerBox
    
    I --> I1["755 (rwxr-xr-x)<br/>📁 Directories & Scripts"]:::exampleBox
    I --> I2["644 (rw-r--r--)<br/>📄 Regular Files"]:::exampleBox
    I --> I3["600 (rw-------)<br/>🔒 Private Files"]:::exampleBox
    I --> I4["777 (rwxrwxrwx)<br/>⚠️ Full Access (Dangerous!)"]:::exampleBox
    
    %% Permission Calculation
    J[🧮 Calculate Octal]:::headerBox
    J --> J1["Add the values:<br/>r=4, w=2, x=1<br/><br/>Example: rwx = 4+2+1 = 7<br/>Example: r-x = 4+0+1 = 5<br/>Example: r-- = 4+0+0 = 4"]:::detailBox
    
    %% Directory Special Rules
    K[📁 Directory Permissions]:::headerBox
    K --> K1["📖 Read: List contents"]:::detailBox
    K --> K2["✏️ Write: Create/delete files"]:::detailBox
    K --> K3["⚡ Execute: Enter directory"]:::detailBox
