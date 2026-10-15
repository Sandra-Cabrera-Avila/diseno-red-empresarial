# P-001 — Diseño de una red empresarial para Creavatek

## 1. Descripción del proyecto

Este proyecto consiste en el diseño y la simulación de una red informática para Creavatek, una empresa ficticia. La red se desarrolló en Cisco Packet Tracer con el propósito de organizar los dispositivos por áreas de trabajo, establecer un esquema de direccionamiento IP y permitir la comunicación entre las redes que lo requieren.

Además, se implementaron medidas básicas de segmentación y control de acceso para restringir la comunicación de la red de invitados con las redes internas de la empresa.

## 2. Objetivo

Diseñar, configurar y documentar una red empresarial pequeña mediante una simulación que permita representar su estructura, comprobar la conectividad y aplicar conceptos fundamentales de redes.

## 3. Tecnologías y herramientas

- Cisco Packet Tracer.
- Routers y switches Cisco simulados.
- Redes de área local virtuales (VLAN).
- Direccionamiento IPv4 estático.
- Enrutamiento entre VLAN mediante subinterfaces del router.
- Redes inalámbricas para gerencia e invitados.
- Listas de control de acceso (ACL).
- Pruebas de conectividad mediante `ping`.

## 4. Diseño de la red

La red utiliza una topología en estrella: los dispositivos finales se conectan a un switch central, que a su vez se conecta a un router.

La segmentación lógica se realiza mediante siete VLAN:

| VLAN | Nombre | Subred |
|---:|---|---|
| 10 | Gerencia | 192.168.10.0/24 |
| 20 | Desarrollo | 192.168.20.0/24 |
| 30 | Soporte | 192.168.30.0/24 |
| 40 | Diseño | 192.168.40.0/24 |
| 50 | Administración | 192.168.50.0/24 |
| 60 | Invitados | 192.168.60.0/24 |
| 70 | Servidores | 192.168.70.0/24 |

El router proporciona el enrutamiento entre las VLAN mediante subinterfaces. Se configuró una ACL para impedir que la red de invitados acceda a las subredes internas de la empresa.

## 5. Pruebas realizadas

Durante la simulación se realizaron pruebas de conectividad con los siguientes resultados:

- Comunicación entre un equipo de Desarrollo y su puerta de enlace.
- Comunicación entre Desarrollo y el servidor.
- Comunicación entre Administración y la impresora.
- Conectividad inalámbrica de los equipos de Gerencia con su puerta de enlace.
- Conectividad de la red de Invitados con su puerta de enlace.
- Bloqueo de la comunicación desde Invitados hacia el servidor mediante la ACL.

Las pruebas realizadas confirmaron la conectividad de los destinos permitidos y el bloqueo de la comunicación de invitados hacia las redes internas comprobadas.

## 6. Estructura del repositorio

- `README.md`: presentación general del proyecto.
- `docs/`: documentación de la arquitectura y del direccionamiento IP.
- `simulacion/`: archivo de Cisco Packet Tracer.
- `diagramas/`: diagrama de la topología de red.
- `evidencias/`: capturas de pantalla de la configuración y de las pruebas.

## 7. Alcance y limitaciones

El proyecto representa una red empresarial en un entorno simulado. La configuración y las pruebas documentadas corresponden a los dispositivos y destinos comprobados en Cisco Packet Tracer; no se afirma que todos los equipos hayan sido probados individualmente.

## 8. Autoría

Proyecto académico P-001 — Laboratorio de redes: diseñar y documentar una red empresarial pequeña.
