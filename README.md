Despliegue automático de la pila Elasticsearch
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
│   │       ├── proxyhttpd.conf.j2
│   │       └── proxynginx.conf.j2
└── run.yml
```
El directorio Playbooks contiene procesos en desarrollo.

EJEMPLO MODO DE USO:
---
ansible-playbook run.yml -e "tasks_type=install" -e "version=8"

| Argumentos | Detalles |
| --------- | --------- |
| tasks_type=install | Comienza la instalación |
| tasks_type=remove | Remueve una instalación previa (pendiente) |
| tasks_type=status | Ejecuta "HealCheking" y muestra los resultados (pendiente) |
| version=6 | selecciona los repos 6.x |
| version=7 | selecciona los repos 7.x |
| version=8 | selecciona los repos 8.x |

NOTA:
---
* Se requiere salida a internet para descargar los paquetes del repositorio oficial.
* A la fecha de esta documentación la versión actual de ELK: 8.8.1
* Por defecto incluye una licencia básica para el uso de ELK.
* La configuración esta por defecto desde los repositorios oficiales de ELK
* Considere modificarlos y establecer los parámetros que necesite siguiendo las instrucciones https://www.elastic.co/guide/index.html#viewall

ELK 8:
---
Si realiza la instalación de la versión 8 tome en cuenta los siguientes puntos:
* Cuando finaliza el proceso, tome nota de los resultados finales:
    - New_Token
    - Password de Kibana_System
    - COD2FA
    - Password del usuario Elastic

* Se deben insertar en el sitio de Kibana "http://direccionIP" para finalizar la instalación:
    - inserte el valor del token generado anteriormente
    - pulse el boton "Install manual"
    - pulse el boton "Check Address" (no modifique nada)
    - rellene la contraseña de Kibana_System que se le ha proporcionado en la salida del playbook
    - confirme el certificado de autenticación
    - finalice la instalación confirmando "Configure Elastic"

License:
---
ELK requiere de una licencia. 
Puede solicitar una trial por 30 días ó adquirir la licencia premium con todas las características.
Puede consultar su licencia desde el menú "License Management"

Sistema Operativos suportados:
---
Verificado en los siguientes entornos:

| System | Check |
| ------ | ----- |
| Debian | OK |
| Ubuntu | OK |
| RedHat | OK |
| AlmaLinux | OK |

---
Hardware:
---
Fuente: https://www.elastic.co/guide/en/cloud-enterprise/current/ece-hardware-prereq.html

Memory:
---

| Memory | Coordinators | Directors | Proxies | Allocators |
| ------ | ------------ | --------- | ------- | ---------- |
| Minimum to install | 8 GB RAM | 8 GB RAM | 8 GB RAM | 8 GB RAM |
| Minimum recommended | 16 GB RAM | 8 GB RAM | 8 GB RAM | 128 GB to 256 GB RAM1 |
| Small deployment2	| 32 GB RAM | 32 GB RAM | 16 GB RAM | 128 GB RAM |
| Medium deployment2 | 32 GB RAM | 32 GB RAM | 32 GB RAM | 256 GB RAM |
| Large deployment3 | 128 GB RAM | 128 GB RAM | 128 GB RAM | 256 GB RAM |

Storage:
---

|	Storage	|	Coordinators	|	Directors	|	Proxies	|	Allocators	|
|	 ---	|	 ---	|	 ---	|	 ---	|	 ---	|
|	Minimum to install	|	10 GB	|	10 GB	|	15 GB	|	10 GB	|
|	Minimum recommended	|	1:4 RAM-to-storage ratio1	|	1:4 RAM-to-storage ratio1	|	|1:4 RAM-to-storage ratio1	|	Enough storage to support the RAM-to-storage ratio2	|


Roadmap:
---
* REPOSITORIOS OFICIALES
* PRE-REQUISITOS
* INSTALACION ELS + KIBANA + LOGSTASH
* CERTIFICADOS (omitido)
* IMPORTAR CONFIGURACION ELS ( por defecto )
* IMPORTAR CONFIGURACION KIBANA ( añade: server.publicBaseUrl: "http://localhost" )
* IMPORTAR CONFIGURACION LOGSTASH ( por defecto NOTA: Se recomienda configurar /etc/logstash/config.d/ con los agentes y puertos que requiera )
* INICIAR ELS
* INICIAR KIBANA
* INICIAR LOGSTASH
* PROXY REVERSE HTTP
* TOKEN FOR ENROLLMENT KIBANA
* PASSWORD KIBANA_SYSTEM
* PASS-CODE 2FA VERIFICATION FOR ENROLLMENT KIBANA
* PASSWORD ELS

ABOUT ME
---
Rodrigo Daniel Bedani
rbedani@flexxible.com
DevOps | Flexxible IT
