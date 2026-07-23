# Proyecto de Infraestructura y Telefonía VoIP

Diseño e implementación de una solución de telefonía VoIP mediante **Asterisk**, **Linphone**, **Wireshark** y **Cisco Packet Tracer**.

El proyecto combina la implementación de una central telefónica IP real con el diseño de una red corporativa simulada, segmentada por departamentos y preparada para soportar tráfico de datos y voz.

---

## Descripción general

El proyecto se desarrolló en dos etapas principales.

En la primera etapa se implementó una central telefónica IP utilizando Asterisk sobre Ubuntu Server. Se configuraron extensiones SIP mediante PJSIP, se conectaron clientes Linphone y se realizaron llamadas entre distintos dispositivos.

Posteriormente, el tráfico generado fue capturado y analizado con Wireshark, prestando especial atención a los protocolos SIP y RTP, así como a parámetros de calidad de servicio como jitter, pérdida de paquetes y delay.

En la segunda etapa se diseñó una red empresarial simulada en Cisco Packet Tracer. La red fue dividida en distintos departamentos, con VLANs independientes para datos y voz, telefonía IP, direccionamiento IP, DHCP, routing y servicios de red.

---

## Objetivos

* Implementar una central telefónica IP utilizando Asterisk.
* Configurar extensiones y autenticación SIP mediante PJSIP.
* Conectar clientes de telefonía IP utilizando Linphone.
* Establecer llamadas entre distintos dispositivos.
* Analizar tráfico SIP y RTP mediante Wireshark.
* Evaluar parámetros de calidad de servicio.
* Diseñar una red corporativa segmentada por departamentos.
* Configurar VLANs de datos y voz.
* Implementar direccionamiento IP y asignación automática mediante DHCP.
* Configurar routing entre las distintas redes.
* Integrar telefonía IP dentro de una infraestructura empresarial simulada.
* Documentar la arquitectura, configuración y resultados obtenidos.

---

## Tecnologías utilizadas

### Telefonía VoIP

* Asterisk
* PJSIP
* Linphone
* SIP
* RTP

### Redes e infraestructura

* Cisco Packet Tracer
* VLANs
* Inter-VLAN Routing
* DHCP
* TCP/IP
* Routing
* Telefonía IP

### Análisis de tráfico

* Wireshark
* Captura de paquetes
* Análisis SIP
* Análisis RTP
* Jitter
* Pérdida de paquetes
* Delay

### Virtualización y sistemas operativos

* Ubuntu Server
* VirtualBox
* SSH
* Linux

### Control de versiones y documentación

* Git
* GitHub
* Microsoft Word
* PDF
* Markdown

---

## Arquitectura de la solución

La arquitectura general del proyecto está compuesta por los siguientes elementos:

* Una máquina virtual con Ubuntu Server.
* Una central telefónica IP implementada con Asterisk.
* Extensiones SIP configuradas mediante PJSIP.
* Clientes Linphone instalados en una computadora y un dispositivo móvil.
* Capturas de tráfico realizadas desde Wireshark.
* Una red corporativa simulada en Cisco Packet Tracer.
* Routers, switches, teléfonos IP, computadoras y servidores.
* VLANs independientes para tráfico de datos y voz.
* Servicios DHCP para la asignación automática de direcciones IP.
* Routing entre los distintos departamentos.

---

## Central Asterisk

La central telefónica fue implementada sobre una máquina virtual con Ubuntu Server.

La dirección IP utilizada por la central durante el desarrollo fue:

```text
192.168.0.15
```

Las extensiones principales configuradas fueron:

| Extensión | Dispositivo                    |
| --------- | ------------------------------ |
| 1001      | Computadora con Linphone       |
| 1002      | Dispositivo móvil con Linphone |

Los archivos principales de configuración de Asterisk incluidos en el repositorio son:

```text
asterisk/pjsip.conf
asterisk/extensions.conf
```

### `pjsip.conf`

Este archivo contiene la configuración de:

* Transporte SIP.
* Endpoints.
* Autenticación.
* Address of Record.
* Extensiones SIP.
* Contextos asociados.

### `extensions.conf`

Este archivo contiene el plan de marcado utilizado para establecer llamadas entre las extensiones configuradas.

---

## Diseño de la red corporativa

La red empresarial fue diseñada para representar una organización dividida en cuatro departamentos:

| Departamento | Computadoras | Teléfonos IP |
| ------------ | -----------: | -----------: |
| Finance      |           10 |           10 |
| HR           |           10 |           10 |
| Sales        |           10 |           10 |
| ICT          |           10 |           10 |

Cada departamento cuenta con:

* Una VLAN de datos.
* Una VLAN de voz.
* Direccionamiento IP independiente.
* Acceso a servicios DHCP.
* Comunicación con otros departamentos mediante routing.
* Telefonía IP integrada.

También se incluyó un segmento destinado a servidores y servicios de red.

---

## VLANs

Las VLANs permiten separar lógicamente el tráfico de datos y el tráfico de voz.

Esta segmentación mejora:

* La organización de la red.
* La administración de dispositivos.
* La seguridad.
* El rendimiento.
* La calidad de servicio.
* La escalabilidad.

Ejemplo de segmentación utilizada:

| Departamento |               VLAN de datos | VLAN de voz |
| ------------ | --------------------------: | ----------: |
| Finance      |                          10 |         100 |
| HR           |                          20 |         100 |
| ICT          |                          40 |         100 |
| Sales        | Configurada en la topología |         100 |

---

## Análisis de tráfico

Wireshark fue utilizado para capturar y estudiar el tráfico generado durante las llamadas VoIP.

Los principales protocolos analizados fueron:

### SIP

SIP se utiliza para:

* Registrar las extensiones.
* Iniciar llamadas.
* Negociar sesiones.
* Modificar sesiones.
* Finalizar llamadas.

### RTP

RTP se utiliza para transportar el audio de las llamadas en tiempo real.

Durante el análisis se observaron parámetros como:

* Cantidad de paquetes.
* Dirección IP de origen y destino.
* Puertos UDP.
* Códec utilizado.
* Jitter.
* Pérdida de paquetes.
* Delta entre paquetes.
* Duración de la comunicación.

Uno de los flujos analizados utilizó el códec:

```text
G.711 μ-law
```

Los resultados mostraron una comunicación estable, sin pérdida de paquetes significativa en el escenario de prueba.

---

## Estructura del repositorio

```text
.
├── asterisk
│   ├── extensions.conf
│   └── pjsip.conf
│
├── configs
│   ├── routers
│   │   ├── router-finance.txt
│   │   ├── router-hr.txt
│   │   ├── router-ict.txt
│   │   └── router-sales.txt
│   │
│   └── switches
│       ├── switch-finance.txt
│       ├── switch-hr.txt
│       ├── switch-ict.txt
│       ├── switch-sales.txt
│       └── switch-servers.txt
│
├── informe
│   ├── Informe_Proyecto_VoIP.docx
│   └── Informe_Proyecto_VoIP.pdf
│
├── packet-tracer
│   └── red-disenio.pkt
│
├── wireshark
│   ├── rtp-sequences.yaml
│   └── traffic-analysis-ws.pcapng
│
├── .gitignore
└── README.md
```

---

## Contenido de las carpetas

### `asterisk`

Contiene los archivos principales de configuración de la central telefónica.

### `configs/routers`

Contiene las configuraciones exportadas de los routers de cada departamento.

### `configs/switches`

Contiene las configuraciones de los switches departamentales y del switch de servidores.

### `informe`

Contiene el informe completo del proyecto en formato editable y PDF.

### `packet-tracer`

Contiene la topología completa desarrollada en Cisco Packet Tracer.

### `wireshark`

Contiene la captura de tráfico de red y los resultados del análisis RTP.

---

## Comandos útiles de Asterisk

Para ingresar a la consola de Asterisk:

```bash
sudo asterisk -rvvv
```

Para listar los endpoints configurados:

```asterisk
pjsip show endpoints
```

Para visualizar los dispositivos registrados:

```asterisk
pjsip show contacts
```

Para visualizar llamadas activas:

```asterisk
core show channels
```

Para mostrar el plan de marcado:

```asterisk
dialplan show
```

Para recargar la configuración de PJSIP:

```asterisk
pjsip reload
```

---

## Comandos útiles de Linux

Para visualizar la configuración de PJSIP:

```bash
sudo cat /etc/asterisk/pjsip.conf
```

Para visualizar el plan de marcado:

```bash
sudo cat /etc/asterisk/extensions.conf
```

Para editar la configuración de PJSIP:

```bash
sudo nano /etc/asterisk/pjsip.conf
```

Para editar el plan de marcado:

```bash
sudo nano /etc/asterisk/extensions.conf
```

Para comprobar el estado de Asterisk:

```bash
sudo systemctl status asterisk
```

Para comprobar el estado de SSH:

```bash
sudo systemctl status ssh
```

---

## Resultados

A partir de la implementación realizada se logró:

* Instalar y configurar una central Asterisk funcional.
* Registrar extensiones SIP desde distintos dispositivos.
* Establecer llamadas entre una computadora y un teléfono móvil.
* Capturar tráfico SIP y RTP.
* Analizar parámetros de calidad de comunicación.
* Diseñar una red empresarial segmentada.
* Configurar routers y switches.
* Implementar VLANs de datos y voz.
* Asignar direcciones mediante DHCP.
* Establecer conectividad entre los distintos departamentos.
* Integrar conceptos de telefonía IP, redes, virtualización y análisis de tráfico.

---

## Aprendizajes obtenidos

Este proyecto permitió aplicar conocimientos relacionados con:

* Administración de sistemas Linux.
* Configuración de servicios de red.
* Telefonía sobre IP.
* Protocolos SIP y RTP.
* Configuración de Asterisk.
* Segmentación mediante VLANs.
* Routing y direccionamiento IP.
* Configuración de routers y switches Cisco.
* Captura y análisis de paquetes.
* Diagnóstico de problemas de conectividad.
* Documentación técnica.
* Organización de proyectos de infraestructura.

---

## Posibles mejoras futuras

* Incorporar más extensiones SIP.
* Implementar buzón de voz.
* Configurar un IVR.
* Agregar grabación de llamadas.
* Incorporar seguridad mediante TLS y SRTP.
* Implementar calidad de servicio con QoS.
* Simular pérdida de paquetes y congestión.
* Comparar distintos códecs de audio.
* Incorporar monitoreo mediante Grafana o herramientas similares.
* Automatizar configuraciones mediante Ansible.
* Desplegar la solución en una plataforma cloud.
* Implementar redundancia y alta disponibilidad.
* Integrar una base de datos para el registro de llamadas.
* Incorporar métricas mediante Call Detail Records.

---

## Seguridad

Los archivos de configuración publicados en este repositorio fueron preparados con fines académicos.

Las contraseñas, claves, tokens y demás credenciales sensibles deben reemplazarse por valores de ejemplo antes de publicar el repositorio.

Ejemplo:

```ini
password=CAMBIAR_CONTRASENA
```

No se recomienda utilizar estas configuraciones directamente en un entorno productivo sin aplicar medidas adicionales de seguridad.

---

## Autor

**Tomas Acosta**

Estudiante de Ingeniería Informática.

Intereses principales:

* Infraestructura
* Redes
* Cloud
* DevOps
* Desarrollo de software
* Telecomunicaciones
* Ciberseguridad
* Análisis de datos

---

## Licencia

Este proyecto fue desarrollado con fines académicos y educativos.

