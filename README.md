Despliegue automático de la pila Elasticsearch
---
Automatic deployment of the Elasticsearch stack
---
La siguiente estructura contiene el orden de los elementos que forman parte del rol "Install ELK"

El despliegue ejecuta la instalación de ElasticSearch + Logstash + Kibana

```shell
elk
├── README.md
├── roles
│   ├── install
│   │   ├── tasks
│   │   │   ├── config_repo_debian.yml
│   │   │   ├── config_repo_redhat.yml
│   │   │   ├── import_config_elk.yml
│   │   │   ├── import_license.yml
│   │   │   ├── install_dependencias_debian.yml
│   │   │   ├── install_dependencias_redhat.yml
│   │   │   ├── install_elk_debian.yml
│   │   │   ├── install_elk_redhat.yml
│   │   │   ├── install_proxyhttpd.yml
│   │   │   ├── install_proxynginx.yml
│   │   │   ├── main.yml
│   │   │   ├── notificacion.yml
│   │   │   └── reload_services.yml
│   │   └── templates
│   │       ├── beats-input.conf.j2
│   │       ├── elasticsearch-output.conf.j2
│   │       ├── elasticsearch.conf.j2
│   │       ├── kibana.conf.j2
│   │       ├── logstash.conf.j2
│   │       ├── proxyhttpd.conf.j2
│   │       └── proxynginx.conf.j2
└── run.yml
```

EJEMPLO MODO DE USO:
---
ansible-playbook run.yml -e "Install=true" -e "version=7"

| Argumentos | Detalles |
| --------- | --------- |
| install=true | Comienza la instalación |
| remove=true | Remueve una instalación previa (pendiente) |
| status=true | Ejecuta "HealCheking" y muestra los resultados (pendiente) |
| version=6 | selecciona los repos 6.x |
| version=7 | selecciona los repos 7.x (recomendado)|
| version=8 | selecciona los repos 8.x |

NOTA:
---
* Se requiere salida a internet para descargar los paquetes del repositorio oficial.
* A la fecha de esta documentación la versión actual de ELK: 8.8.1 (Requiere licencia)
* En esta instancia incluye una licencia básica para la versión de ELK.

ELK 8:
---
Si realiza la instalación de la versión 8 tome en cuenta los siguientes puntos:
* Cuando finaliza el proceso, tome nota de los resultados finales
* La password del usuario Elastic, Kibana_System, El nuevo token para kibana, y el Código 2FA de doble autenticación.
* Se deben insertar en el sitio de Kibana para finalizar la instalación, pulse el boton instalación manual y rellene los datos de usuario y contraseña Kibana_System que se le ha proporcionado en la salida del playbook.


Posiblemente a futuro tengamos el proceso automatizado al 100%

License:
---
ELK requiere de una licencia para permanecer con las funciones básicas ó puede solicitar la trial por 30 días o comprar la licencia premium.
Puede registrar su licencia desde el menú "License Management"

Verificado en los siguientes entornos:
---

Sistema Operativos suportados:
---
| System | Check |
| ------ | ----- |
| Debian | OK |
| Ubuntu | OK |
| RedHat | OK |
| AlmaLinux | OK |

Requisitos:
---
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
