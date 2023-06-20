Despliegue automático de la pila Elasticsearch
---
Automatic deployment of the Elasticsearch stack
---
La siguiente estructura contiene el orden de los elementos que forman parte del rol "Install ELK"

El despliegue ejecuta la instalacion de ElasticSearch + Logstash + Kibana

```shell
elk
├── README.md
├── playbooks
│   ├── almalinux.yml
│   ├── delete.yml
│   ├── healcheck.yml
│   ├── install copy.yml
│   ├── install-agents.yml
│   ├── install-config-elk.yml
│   ├── install-config-kibana.yml
│   ├── install-dependency.yml
│   ├── install-download.yml
│   ├── install-elk.yml
│   ├── install-kibana.yml
│   ├── install-proxyhttpd.yml
│   ├── install-proxynginx.yml
│   ├── install-redhat.yml
│   ├── install-ubuntu.yml
│   ├── install-user.yml
│   ├── licencia.yml
│   ├── pendiente-crear_usuario.yml
│   ├── reload.yml
│   └── remove.yml
├── roles
│   ├── healcheking
│   │   └── tasks
│   │       └── main.yml
│   ├── install
│   │   ├── files
│   │   │   └── license.json
│   │   └── tasks
│   │       ├── config_elk.yml
│   │       ├── config_repo_debian.yml
│   │       ├── config_repo_redhat.yml
│   │       ├── dependencias_debian.yml
│   │       ├── dependencias_redhat.yml
│   │       ├── install_debian.yml
│   │       ├── install_redhat.yml
│   │       ├── main.yml
│   │       ├── notificacion.yml
│   │       ├── proxyhttpd.yml
│   │       ├── proxynginx.yml
│   │       └── services.yml
│   ├── remove
│   │   └── tasks
│   │       └── main.yml
│   └── templates
│       ├── beats-input.conf.j2
│       ├── elasticsearch-output.conf.j2
│       ├── elasticsearch.conf.j2
│       ├── kibana.conf.j2
│       ├── logstash.conf.j2
│       ├── proxyhttpd.conf.j2
│       └── proxynginx.conf.j2
└── run.yml
```

MODO DE USO:
---
ansible-playbook run.yml -e "Install=true"

| Argumentos | Detalles |
| --------- | --------- |
| Install=true | Comienza la instalacion |
| Remove=true | Remueve una instalacion previa |
| Status=true | Ejecuta HealCheking y muestra los resultados |

Cuando finaliza el proceso, tome nota de los resultados finales

La password del usuario Elastic, Kibana_System, El nuevo token para kibana, y el Codigo 2FA de doble autenticacion.
Se deben insertar en el sitio de Kibana para finalizar la instalacion.

Posiblemente a futuro tengamos el proceso automatizado al 100%

Se recomienda generar un nuevo usuario Admin desde el menu Stack Management

* Se requiere salida a internet para descargar los paquetes del repositorio oficial.
* A la fecha de esta documentacion la version actual de ELK: 8.8.1
Verificado en los siguientes entornos:

| System | Check |
| ------ | ----- |
| Debian | OK |
| RedHat | OK |
| AlmaLinux | OK |

CPU: 2 Cores
RAM: 4 GiB
DISK: 64 GiB

Roadmap:
---
### REPOSITORIOS OFICIALES
### PRE-REQUISITOS
### INSTALACION ELS + KIBANA + LOGSTASH
### CERTIFICADOS (omitido)
### IMPORTAR CONFIGURACION ELS
### IMPORTAR CONFIGURACION KIBANA
### IMPORTAR CONFIGURACION LOGSTASH
### INICIAR ELS
### INICIAR KIBANA
### INICIAR LOGSTASH
### PROXY REVERSE HTTP
### TOKEN FOR ENROLLMENT KIBANA
### PASS-CODE 2FA VERIFICATION FOR ENROLLMENT KIBANA
### PASSWORD ELS
### PASSWORD KIBANA_SYSTEM
### API - ADD USER/PASSWORD ADMIN (pendiente)

ABOUT ME
---
Rodrigo Daniel Bedani
rbedani@flexxible.com
DevOps | Flexxible IT