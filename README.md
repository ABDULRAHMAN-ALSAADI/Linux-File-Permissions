```mermaid
flowchart TD
    %% Styling with larger elements
    classDef headerBox fill:#2563eb,stroke:#1d4ed8,stroke-width:3px,color:#ffffff,font-weight:bold,font-size:16px
    classDef conceptBox fill:#10b981,stroke:#059669,stroke-width:3px,color:#ffffff,font-weight:bold,font-size:14px
    classDef detailBox fill:#f59e0b,stroke:#d97706,stroke-width:2px,color:#ffffff,font-size:13px
    classDef commandBox fill:#8b5cf6,stroke:#7c3aed,stroke-width:2px,color:#ffffff,font-size:13px
    classDef exampleBox fill:#ef4444,stroke:#dc2626,stroke-width:2px,color:#ffffff,font-size:13px
    classDef calcBox fill:#06b6d4,stroke:#0891b2,stroke-width:2px,color:#ffffff,font-size:13px
    
    %% MAIN HEADER
    A["🐧 LINUX FILE PERMISSIONS<br/>Complete Reference Guide"]:::headerBox
    
    %% SECTION 1: PERMISSION TYPES
    A --> B["📋 PERMISSION TYPES<br/>What each permission means"]:::conceptBox
    
    B --> B1["📖 READ PERMISSION (r)<br/>Binary: 100 | Octal: 4<br/>• Files: View content<br/>• Directories: List contents"]:::detailBox
    
    B --> B2["✏️ WRITE PERMISSION (w)<br/>Binary: 010 | Octal: 2<br/>• Files: Modify content<br/>• Directories: Create/delete files"]:::detailBox
    
    B --> B3["⚡ EXECUTE PERMISSION (x)<br/>Binary: 001 | Octal: 1<br/>• Files: Run as program<br/>• Directories: Enter directory"]:::detailBox
    
    %% SECTION 2: USER CATEGORIES
    B1 --> C["👥 USER CATEGORIES<br/>Who gets these permissions"]:::conceptBox
    B2 --> C
    B3 --> C
    
    C --> C1["👤 OWNER (u)<br/>The file creator<br/>Usually the user who made the file"]:::detailBox
    
    C --> C2["👥 GROUP (g)<br/>Users in assigned group<br/>Share permissions with others"]:::detailBox
    
    C --> C3["🌍 OTHERS (o)<br/>Everyone else<br/>All other system users"]:::detailBox
    
    %% SECTION 3: VIEWING PERMISSIONS
    C1 --> D["👀 VIEWING PERMISSIONS<br/>How to check current permissions"]:::conceptBox
    C2 --> D
    C3 --> D
    
    D --> D1["📋 LS COMMAND<br/>ls -l filename<br/>Shows: -rwxr-xr-x 1 user group 1234 date filename"]:::commandBox
    
    D --> D2["🔍 PERMISSION STRING BREAKDOWN<br/>-rwxr-xr-x<br/>│└┬┘└┬┘└┬┘<br/>│ │  │  └── Others permissions<br/>│ │  └───── Group permissions<br/>│ └──────── Owner permissions<br/>└────────── File type (-=file, d=directory)"]:::detailBox
    
    %% SECTION 4: OCTAL CALCULATION
    D1 --> E["🧮 OCTAL CALCULATION<br/>Converting permissions to numbers"]:::conceptBox
    D2 --> E
    
    E --> E1["📊 PERMISSION VALUES<br/>Read (r) = 4<br/>Write (w) = 2<br/>Execute (x) = 1<br/>No permission (-) = 0"]:::calcBox
    
    E --> E2["🔢 CALCULATION EXAMPLES<br/>rwx = 4+2+1 = 7<br/>rw- = 4+2+0 = 6<br/>r-x = 4+0+1 = 5<br/>r-- = 4+0+0 = 4<br/>-wx = 0+2+1 = 3<br/>-w- = 0+2+0 = 2<br/>--x = 0+0+1 = 1<br/>--- = 0+0+0 = 0"]:::calcBox
    
    %% SECTION 5: CHANGING PERMISSIONS
    E1 --> F["🔧 CHANGING PERMISSIONS<br/>Using chmod command"]:::conceptBox
    E2 --> F
    
    F --> F1["📝 SYMBOLIC METHOD<br/>chmod [who][operation][permission] file<br/><br/>Examples:<br/>chmod u+x script.sh    # Add execute for owner<br/>chmod g-w document.txt # Remove write for group<br/>chmod o=r config.file  # Set others to read-only<br/>chmod a+r readme.txt   # Add read for all<br/>chmod ug+w,o-r file    # Multiple operations"]:::commandBox
    
    F --> F2["🔢 OCTAL METHOD<br/>chmod [owner][group][others] file<br/><br/>Examples:<br/>chmod 755 script.sh    # rwxr-xr-x<br/>chmod 644 document.txt # rw-r--r--<br/>chmod 600 private.key  # rw-------<br/>chmod 777 shared_dir   # rwxrwxrwx (dangerous!)<br/>chmod 444 readonly.txt # r--r--r--"]:::commandBox
    
    %% SECTION 6: COMMON PERMISSION SETS
    F1 --> G["🎯 COMMON PERMISSION SETS<br/>Standard permission patterns"]:::conceptBox
    F2 --> G
    
    G --> G1["📁 DIRECTORIES<br/>755 (rwxr-xr-x)<br/>• Owner: full access<br/>• Group & Others: read and enter<br/>• Most common for directories"]:::exampleBox
    
    G --> G2["📄 REGULAR FILES<br/>644 (rw-r--r--)<br/>• Owner: read and write<br/>• Group & Others: read only<br/>• Most common for files"]:::exampleBox
    
    G --> G3["📜 EXECUTABLE FILES<br/>755 (rwxr-xr-x)<br/>• Owner: full access<br/>• Group & Others: read and execute<br/>• For scripts and programs"]:::exampleBox
    
    G --> G4["🔒 PRIVATE FILES<br/>600 (rw-------)<br/>• Owner: read and write<br/>• Group & Others: no access<br/>• For sensitive files"]:::exampleBox
    
    G --> G5["⚠️ FULL ACCESS<br/>777 (rwxrwxrwx)<br/>• Everyone: full access<br/>• SECURITY RISK - avoid!<br/>• Only use temporarily if needed"]:::exampleBox
    
    %% SECTION 7: OWNERSHIP CHANGES
    G1 --> H["👑 CHANGING OWNERSHIP<br/>Managing file ownership"]:::conceptBox
    G2 --> H
    G3 --> H
    G4 --> H
    G5 --> H
    
    H --> H1["🔄 CHOWN COMMAND<br/>chown [user]:[group] file<br/><br/>Examples:<br/>chown alice:developers file.txt<br/>chown bob: script.sh        # Change user only<br/>chown :admin config.file    # Change group only<br/>chown -R user:group dir/    # Recursive for directories"]:::commandBox
    
    H --> H2["👥 CHGRP COMMAND<br/>chgrp [group] file<br/><br/>Examples:<br/>chgrp developers project.txt<br/>chgrp -R admin /var/log/    # Recursive"]:::commandBox
    
    %% SECTION 8: SPECIAL PERMISSIONS
    H1 --> I["⭐ SPECIAL PERMISSIONS<br/>Advanced permission concepts"]:::conceptBox
    H2 --> I
    
    I --> I1["🔐 SETUID (4000)<br/>Run with owner's privileges<br/>Example: chmod 4755 program<br/>Shows as: rwsr-xr-x"]:::detailBox
    
    I --> I2["🔐 SETGID (2000)<br/>Run with group's privileges<br/>Example: chmod 2755 program<br/>Shows as: rwxr-sr-x"]:::detailBox
    
    I --> I3["📌 STICKY BIT (1000)<br/>Only owner can delete<br/>Example: chmod 1755 directory<br/>Shows as: rwxr-xr-t<br/>Common on /tmp directory"]:::detailBox
    
    %% FINAL SUMMARY
    I1 --> J["✅ QUICK REFERENCE<br/>Most used commands"]:::headerBox
    I2 --> J
    I3 --> J
    
    J --> J1["📋 ESSENTIAL COMMANDS<br/>ls -l file          # View permissions<br/>chmod 755 file      # Set permissions<br/>chmod u+x file      # Add execute<br/>chown user:group    # Change ownership<br/>find . -perm 777    # Find files with 777"]:::commandBox
