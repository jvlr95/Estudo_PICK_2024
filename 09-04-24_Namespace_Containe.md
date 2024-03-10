# Conteinerização no Linux

## Conceito de Contêiner
- **Objetivo**: Isolar recursos para uma finalidade específica.
- **Isolamento de Recursos**:
  - Filesystem
  - Processos (PID)
  - CPU, Memória e Usuário

## Ferramentas do Kernel Linux
- **CGroups v1 e v2**:
  - Isolam recursos (Namespaces)
  - Limitam recursos (CGroup)

## Funcionalidades Principais
- **Namespaces**:
  - Isolam diversos recursos:
    - Filesystem
    - PID
    - Network
    - Usuários

- **CGroups**:
  - Limitam recursos como CPU e Memória

- **Chroot**:
  - Isola um usuário (Jail user)

## Ferramentas para Containers
- Docker
- LXC:
  - Usa Chroot, Namespaces e CGroups
- Solaris Zones
- Jails (FreeBSD)
- OpenVZ
- VIRTUOSO

## Procedimentos
- Instalação do Debian com debootstrap:
  ```bash
  sudo deboostrap stable /debian http://deb.debian.org/debian
  ```
- Trabalhando com Namespaces:
  ```bash
  sudo unshare --mount --uts --ipc --map-root-user --user --fork --net chroot ./debian bash
  ```

## Recursos Adicionais
- **Documentação** sobre CGroups v2: [Link](https://access.redhat.com/documentation/de-de/red_hat_enterprise_linux/8/html/managing_monitoring_and_updating_the_kernel/using-cgroups-v2-to-control-distribution-of-cpu-time-for-applications_managing-monitoring-and-updating-the-kernel)

- **Trabalhando com CGroups**:
  - Instale as ferramentas cgroup-tools
  - Criar recursos isolados:
    ```bash
    sudo cgcreate -g cpu,memory:/darkstar
    ```
  - Atualizar o PID do container chroot para o mesmo do host:
    ```bash
    sudo cgclassify -g cpu,memory:darkstar <PID>
    ```


