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

Se realizaron pruebas de conectividad y verificación de la red en Cisco Packet Tracer:

- *Desarrollo → servidor:* se recibieron 3 de 4 respuestas, con una pérdida del 25 %.
- *Invitados → servidor:* no se recibieron respuestas (0 de 4 paquetes), con una pérdida del 100 % y mensajes de destino inalcanzable desde 192.168.60.1.
- *VLAN y enlace troncal:* se recopilaron evidencias de los comandos de verificación de Cisco IOS.
- *Conectividad inalámbrica:* se prepararon evidencias de los equipos de Gerencia e Invitados.

Los resultados corresponden a las pruebas documentadas. El bloqueo por ACL debe confirmarse mediante la revisión de su configuración y aplicación.

## 6. Estructura del repositorio

- `README.md`: descripción general, objetivos y alcance del proyecto.
- `Simulacion/`: archivo del proyecto de Cisco Packet Tracer.
- `Evidencias/`: capturas de las pruebas de conectividad, el bloqueo observado desde Invitados, la conexión Wi-Fi de Gerencia y la topología.
- `Diagramas/`: diagrama completo de la topología de red.
- `Informe/`: informe técnico del proyecto en Word y PDF.

## 7. Alcance y limitaciones

El proyecto representa una red empresarial en un entorno simulado. La configuración y las pruebas documentadas corresponden a los dispositivos y destinos comprobados en Cisco Packet Tracer; no se afirma que todos los equipos hayan sido probados individualmente.

## 8. Autoría

Proyecto académico P-001 — Laboratorio de redes: diseñar y documentar una red empresarial pequeña.
