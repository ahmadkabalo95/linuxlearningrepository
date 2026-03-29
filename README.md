%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#007bff', 'edgeLabelBackground':'#f4f4f4', 'tertiaryColor': '#fff'}}}%%

graph TD
    %% Define external entity
    User[<i class='fa fa-user'></i> User / Admin]

    %% Define physical hardware cluster
    subgraph Physical_Hardware [Hypervisor Cluster]
        style Physical_Hardware fill:#eee,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5

        %% Proxmox Host
        PVE[<i class='fa fa-server'></i> Proxmox VE Host<br>(Bare Metal)]

        %% Logical connection (Virtualization)
        PVE -.- Virtual_Machines

        %% Subgraph for VMs and Containers
        subgraph Virtual_Machines [Virtualized Environment]
            style Virtual_Machines fill:#fefefe,stroke:#999,stroke-width:1px

            %% Network & Management Services
            subgraph Mgmt_Net_Services [Infrastructure & Networking]
                style Mgmt_Net_Services fill:#e3f2fd,stroke:#90caf9
                DNS[<i class='fa fa-globe'></i> BIND DNS]
                DHCP[<i class='fa fa-network-wired'></i> DHCP Server]
                Ansible[<i class='fa fa-cogs'></i> Ansible Admin Node]
            end

            %% Security & Control Services
            subgraph Security_Control [Security & Control]
                style Security_Control fill:#e8f5e9,stroke:#a5d6a7
                Gitea[<i class='fa fa-code-branch'></i> Gitea (Version Control)]
                Lynis[<i class='fa fa-shield-alt'></i> Lynis Audit Scripts]
                %% Automation relationship
                Ansible -- Manages --> Gitea
                Ansible -- Deploys --> Docker_Host_Ubuntu
                Ansible -- Deploys --> Docker_Host_RHEL
            end

            %% Application Hosting
            subgraph App_Hosting [Container Ecosystem]
                style App_Hosting fill:#fff3e0,stroke:#ffcc80

                %% Ubuntu Docker Host
                Docker_Host_Ubuntu[<i class='fa fa-ubuntu'></i> Ubuntu VM<br>(Docker Host)]
                subgraph Ubuntu_Docker [Docker Containers (Debian)]
                    style Ubuntu_Docker fill:#fff,stroke:#bbb,stroke-width:1px
                    Portainer[<i class='fa fa-ship'></i> Portainer]
                    MySQL[<i class='fa fa-database'></i> MySQL DB]
                end

                %% RedHat Docker Host
                Docker_Host_RHEL[<i class='fa fa-redhat'></i> RHEL/Rocky VM<br>(Docker Host)]
                subgraph RHEL_Docker [Docker Containers (RHEL)]
                    style RHEL_Docker fill:#fff,stroke:#bbb,stroke-width:1px
                    NPM[<i class='fa fa-random'></i> Nginx Proxy Manager]
                    Homarr[<i class='fa fa-home'></i> Homarr Dashboard]
                end
                
                %% Connect Docker Hosts to their containers logically
                Docker_Host_Ubuntu -- Orchestrates --> Ubuntu_Docker
                Docker_Host_RHEL -- Orchestrates --> RHEL_Docker
            end
        end
    end

    %% Network Flow
    User -->|Accesses via VPN/Local| NPM
    NPM -->|Routes traffic to| Homarr
    NPM -->|Routes traffic to| Portainer
    NPM -->|Connects to| MySQL
    
    Portainer -.->|Manages Containers on| Ubuntu_Docker
    Portainer -.->|Manages Containers on| RHEL_Docker
