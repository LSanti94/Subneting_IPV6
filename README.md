# Subneting

## Introducción a IPv6
---
¿Porque se saltaron de IPV4 a IPV6 y dejaron de lado IPV5?
En realidad en teroria si existe el IPV5 conocido como:

### Internet Stream Protocol Version 2 (ST2) Lo podemos encontrar en el ```RFC 1819```
---

## Caracteristicas
---

- Cambio de Longitud

| Protocolo | Longitud |
|-----------|----------|
| IPv6      | 128 bits |
| IPv4      | 32 bits  |


- Comunicación Anycast: Envia paquetes a un nodo que pertenece a un grupo de nodos
- Scope o Ámbito
- Simplificación de la cabecera: Esto reduce el costo de procesamiento de nodos y en routers

# Comparación entre Encabezado IPv4 e IPv6

| Campo         | IPv4                  | IPv6                |
|---------------|-----------------------|---------------------|
| <span style="color:orange">Version</span>       | <span style="color:orange">**Version**</span>            | <span style="color:orange">**Version**</span>         |
| <span style="color:gray">IHL</span>           | <span style="color:gray">**IHL**</span>                |                     |
| <span style="color:blue">Type of Service</span> | <span style="color:blue">**Type of Service**</span>    | <span style="color:blue">**Traffic Class**</span>   |
| <span style="color:blue">Total Length</span>  | <span style="color:blue">**Total Length**</span>       | <span style="color:blue">**Payload Length**</span>  |
| <span style="color:gray">Identification</span>| <span style="color:gray">**Identification**</span>     |                     |
| <span style="color:gray">Flags</span>         | <span style="color:gray">**Flags**</span>              |                     |
| <span style="color:gray">Fragment Offset</span> | <span style="color:gray">**Fragment Offset**</span>  |                     |
| <span style="color:blue">Time to Live</span>  | <span style="color:blue">**Time to Live**</span>       | <span style="color:blue">**Hop Limit**</span>       |
| <span style="color:blue">Protocol</span>      | <span style="color:blue">**Protocol**</span>           | <span style="color:blue">**Next Header**</span>     |
| <span style="color:gray">Header Checksum</span> | <span style="color:gray">**Header Checksum**</span>  |                     |
| <span style="color:orange">Source Address</span> | <span style="color:orange">**Source Address**</span>    | <span style="color:orange">**Source Address**</span>  |
| <span style="color:orange">Destination Address</span> | <span style="color:orange">**Destination Address**</span> | <span style="color:orange">**Destination Address**</span> |
| <span style="color:gray">Options</span>       | <span style="color:gray">**Options**</span>            |                     |
| <span style="color:gray">Padding</span>       | <span style="color:gray">**Padding**</span>            |                     |
|               |                       | <span style="color:green">**Flow Label**</span> (nuevo en IPv6) |

## Leyenda
- <span style="color:orange">**Campos en naranja**</span>: Nombres de campos que se mantuvieron de IPv4 a IPv6.
- <span style="color:gray">**Campos en gris**</span>: Campos que no se mantienen en IPv6.
- <span style="color:blue">**Campos en azul**</span>: Campos con nombre y posición cambiados en IPv6.
- <span style="color:green">**Campo nuevo en verde**</span>: Campos nuevos en IPv6.

- Etiqueta de Flujo para QoS

| Bits       | Campo           | Descripción                          |
|------------|-----------------|--------------------------------------|
| 0 - 4      | <span style="color: green;">**Version**</span>      | Versión del protocolo (IPv6)         |
| 4 - 12     | <span style="color: blue;">**Traffic Class**</span> | Calidad de servicio (QoS)            |
| 12 - 32    | <span style="color: purple;">**Flow Label**</span>   | Manejo de flujo de paquetes          |
| 32 - 48    | <span style="color: pink;">**Payload Length**</span> | Longitud del payload                 |
| 48 - 56    | <span style="color: red;">**Next Header**</span>     | Tipo de protocolo en el payload      |
| 56 - 64    | <span style="color: orange;">**Hop Limit**</span>    | Límite de saltos (TTL en IPv4)       |
| 64 - 192   | <span style="color: yellow;">**Source Address**</span>| Dirección de origen (128 bits)       |
| 192 - 320  | <span style="color: green;">**Destination Address**</span> | Dirección de destino (128 bits) |


- Extension Headers: 
| Order         | Header Type                                      | Next Header Code |
|---------------|--------------------------------------------------|------------------|
| 1             | Basic IPv6 Header                                | -                |
| 2             | Hop-by-Hop Options                               | 0                |
| 3             | Destination Options (with Routing Options)        | 60               |
| 4             | Routing Header                                   | 43               |
| 5             | Fragment Header                                  | 44               |
| 6             | Authentication Header                            | 51               |
| 7             | Encapsulation Security Payload Header            | 50               |
| 8             | Destination Options                              | 60               |
| 9             | Mobility Header                                  | 135              |
|               | No next header                                   | 59               |
| Upper Layer   | TCP                                              | 6                |
| Upper Layer   | UDP                                              | 17               |
| Upper Layer   | ICMPv6                                           | 58               |
