# Arquitectura de red — Creavatek

## 1. Introducción

Este documento describe la arquitectura lógica y física de la red empresarial simulada para Creavatek. Se detallan la topología, los dispositivos principales, la segmentación de la red y los mecanismos utilizados para permitir o restringir la comunicación entre las distintas áreas.

La implementación se realizó en Cisco Packet Tracer.

## 2. Topología de red

Se utiliza una topología física en estrella. Los dispositivos finales se conectan a un switch central, y este se conecta a un router que permite la comunicación entre las redes virtuales configuradas.

El enlace entre el switch y el router funciona como un enlace troncal (*trunk*), que transporta el tráfico de las VLAN configuradas.

### Componentes principales

- **Router R1-CREAVATEK:** proporciona las puertas de enlace y el enrutamiento entre VLAN mediante subinterfaces.
- **Switch SW1-CREAVATEK:** conecta los equipos finales y asigna los puertos a las VLAN correspondientes.
- **Servidor SRV1-CREAVATEK:** se encuentra en la VLAN 70, destinada a servidores.
- **Impresora PRN1-CREAVATEK:** se encuentra en la VLAN 50, correspondiente a Administración.
- **Puntos de acceso inalámbrico:** proporcionan conectividad inalámbrica para Gerencia e Invitados.
- **Equipos finales:** computadoras de escritorio y laptops distribuidas entre las áreas representadas.

## 3. Distribución de dispositivos

La simulación contiene 28 dispositivos:

| Tipo de dispositivo | Cantidad |
|---|---:|
| Router | 1 |
| Switch | 1 |
| Servidor | 1 |
| Impresora | 1 |
| Puntos de acceso inalámbrico | 2 |
| Computadoras de escritorio | 19 |
| Laptops | 3 |
| **Total** | **28** |

## 4. Segmentación lógica

La red se divide en siete VLAN para separar el tráfico según el área o la función de los dispositivos.

| VLAN | Nombre | Función |
|---:|---|---|
| 10 | GERENCIA | Equipos de gerencia y acceso inalámbrico de esta área |
| 20 | DESARROLLO | Equipos del área de desarrollo |
| 30 | SOPORTE | Equipos del área de soporte |
| 40 | DISENO | Equipos del área de diseño |
| 50 | ADMINISTRACION | Equipos administrativos e impresora |
| 60 | INVITADOS | Dispositivos inalámbricos de invitados |
| 70 | SERVIDORES | Servidor de la empresa |

La segmentación permite organizar la red y establecer políticas de comunicación entre las subredes. La pertenencia a una VLAN se determina por la configuración de los puertos del switch y, para los equipos inalámbricos, por la conexión al punto de acceso correspondiente.

## 5. Enrutamiento entre VLAN

Se configuró el método conocido como *router-on-a-stick*. Consiste en utilizar un enlace troncal entre el switch y el router, junto con una subinterfaz del router para cada VLAN.

Cada subinterfaz tiene una dirección IP que funciona como puerta de enlace de su subred. De esta manera, el router puede encaminar tráfico entre las VLAN, sujeto a las reglas de control de acceso configuradas.

## 6. Red inalámbrica

Se configuraron dos redes inalámbricas:

- **CREAVATEK-GERENCIA:** destinada a los dispositivos inalámbricos de Gerencia y asociada a la VLAN 10.
- **CREAVATEK-INVITADOS:** destinada a los dispositivos invitados y asociada a la VLAN 60.

Ambas redes utilizan protección WPA2-PSK. La separación entre ellas permite aplicar políticas diferentes al tráfico de gerencia y al de invitados.

## 7. Control de acceso

Se configuró una lista de control de acceso extendida denominada `BLOQUEO-INVITADOS` en el router.

La ACL bloquea el tráfico IP originado en la subred 192.168.60.0/24 hacia las subredes internas correspondientes a las VLAN 10, 20, 30, 40, 50 y 70. El resto del tráfico IP se permite mediante la regla final de la lista.

La ACL se aplica en sentido de entrada en la subinterfaz correspondiente a la VLAN 60.

En las pruebas realizadas, el equipo de invitados pudo comunicarse con su puerta de enlace, pero no pudo alcanzar el servidor de la VLAN 70. Esto confirmó el bloqueo del tráfico probado.

## 8. Verificación de conectividad

Se realizaron pruebas con el comando `ping` para comprobar:

- La comunicación de equipos con sus puertas de enlace.
- La conectividad entre Desarrollo y el servidor.
- La conectividad entre Administración y la impresora.
- La conectividad de equipos inalámbricos de Gerencia.
- El bloqueo de acceso desde Invitados hacia el servidor.

Los resultados de estas pruebas se documentarán mediante capturas de pantalla en la carpeta `evidencias/`.

## 9. Consideraciones

La arquitectura corresponde a una simulación académica. Las pruebas realizadas validan los destinos y escenarios indicados, pero no implican que todos los dispositivos o todos los posibles flujos de comunicación hayan sido probados individualmente.

El diseño puede ampliarse en el futuro con servicios adicionales, administración de direcciones IP automatizada, resolución de nombres y reglas de acceso más específicas, si los requisitos del proyecto lo necesitan.
