# Plan de direccionamiento IP — Creavatek

## 1. Objetivo

Este documento presenta el esquema de direccionamiento IPv4 utilizado en la red simulada de Creavatek. Las redes se organizan mediante VLAN para separar las áreas de trabajo y los servicios de la empresa.

## 2. Plan de direccionamiento por VLAN

Se utiliza una máscara de subred `255.255.255.0` (`/24`) en todas las VLAN.

| VLAN | Área o función | Dirección de red | Máscara | Puerta de enlace |
|---:|---|---|---|---|
| 10 | Gerencia | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1 |
| 20 | Desarrollo | 192.168.20.0/24 | 255.255.255.0 | 192.168.20.1 |
| 30 | Soporte | 192.168.30.0/24 | 255.255.255.0 | 192.168.30.1 |
| 40 | Diseño | 192.168.40.0/24 | 255.255.255.0 | 192.168.40.1 |
| 50 | Administración | 192.168.50.0/24 | 255.255.255.0 | 192.168.50.1 |
| 60 | Invitados | 192.168.60.0/24 | 255.255.255.0 | 192.168.60.1 |
| 70 | Servidores | 192.168.70.0/24 | 255.255.255.0 | 192.168.70.1 |

La puerta de enlace de cada subred está configurada en la subinterfaz del router asociada a su VLAN.

## 3. Direcciones IP de los dispositivos

Las siguientes direcciones corresponden a los equipos configurados con direccionamiento estático.

### 3.1 Gerencia

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| LAP-GER-01 | 192.168.10.10 | 192.168.10.1 |
| LAP-GER-02 | 192.168.10.11 | 192.168.10.1 |

### 3.2 Desarrollo

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| PC-DES-01 | 192.168.20.10 | 192.168.20.1 |
| PC-DES-02 | 192.168.20.11 | 192.168.20.1 |
| PC-DES-03 | 192.168.20.12 | 192.168.20.1 |
| PC-DES-04 | 192.168.20.13 | 192.168.20.1 |
| PC-DES-05 | 192.168.20.14 | 192.168.20.1 |
| PC-DES-06 | 192.168.20.15 | 192.168.20.1 |
| PC-DES-07 | 192.168.20.16 | 192.168.20.1 |
| PC-DES-08 | 192.168.20.17 | 192.168.20.1 |

### 3.3 Soporte

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| PC-SOP-01 | 192.168.30.10 | 192.168.30.1 |
| PC-SOP-02 | 192.168.30.11 | 192.168.30.1 |
| PC-SOP-03 | 192.168.30.12 | 192.168.30.1 |
| PC-SOP-04 | 192.168.30.13 | 192.168.30.1 |

### 3.4 Diseño

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| PC-DIS-01 | 192.168.40.10 | 192.168.40.1 |
| PC-DIS-02 | 192.168.40.11 | 192.168.40.1 |
| PC-DIS-03 | 192.168.40.12 | 192.168.40.1 |
| PC-DIS-04 | 192.168.40.13 | 192.168.40.1 |

### 3.5 Administración

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| PC-ADM-01 | 192.168.50.10 | 192.168.50.1 |
| PC-ADM-02 | 192.168.50.11 | 192.168.50.1 |
| PC-ADM-03 | 192.168.50.12 | 192.168.50.1 |
| PRN1-CREAVATEK | 192.168.50.20 | 192.168.50.1 |

### 3.6 Invitados

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| LAP-INV-01 | 192.168.60.10 | 192.168.60.1 |

### 3.7 Servidores

| Dispositivo | Dirección IP | Puerta de enlace |
|---|---|---|
| SRV1-CREAVATEK | 192.168.70.10 | 192.168.70.1 |

## 4. Parámetros generales

- **Tipo de direccionamiento:** IPv4 estático.
- **Máscara de subred:** 255.255.255.0.
- **Prefijo:** /24.
- **DNS:** no se documenta una dirección DNS porque no se indicó una configuración DNS específica en la simulación.

## 5. Observaciones

Las direcciones de red terminadas en `.0` identifican cada subred y las direcciones terminadas en `.1` se reservan como puertas de enlace en este diseño.

Este documento recoge las direcciones registradas para los equipos finales. Antes de considerar el inventario completo, deben verificarse las direcciones de todos los dispositivos en Cisco Packet Tracer.

