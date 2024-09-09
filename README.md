# Subnetting

## Introducción a IPv6

¿Por qué se pasó de IPv4 a IPv6 y se dejó de lado IPv5?  
En realidad, en teoría, sí existe IPv5, conocido como:

### Internet Stream Protocol Version 2 (ST2)  
Lo podemos encontrar en el `RFC 1819`

## Características

- **Cambio de Longitud**

  | Protocolo | Longitud |
  |-----------|----------|
  | IPv6      | 128 bits |
  | IPv4      | 32 bits  |

- **Comunicación Anycast**: Envía paquetes a un nodo que pertenece a un grupo de nodos.
- **Scope o Ámbito**
- **Simplificación de la cabecera**: Esto reduce el costo de procesamiento en nodos y routers.

# Comparación entre Encabezado IPv4 e IPv6

| Campo                       | IPv4                           | IPv6                           |
|-----------------------------|--------------------------------|--------------------------------|
| **Versión**                 | **Versión**                     | **Versión**                     |
| **IHL**                     | **IHL**                         |                                |
| **Tipo de Servicio**        | **Tipo de Servicio**            | **Traffic Class**               |
| **Longitud Total**          | **Longitud Total**              | **Payload Length**              |
| **Identificación**          | **Identificación**              |                                |
| **Flags**                   | **Flags**                       |                                |
| **Fragment Offset**         | **Fragment Offset**             |                                |
| **Tiempo de Vida**          | **Tiempo de Vida**              | **Hop Limit**                   |
| **Protocolo**               | **Protocolo**                   | **Next Header**                 |
| **Checksum de Encabezado**  | **Checksum de Encabezado**      |                                |
| **Dirección de Origen**     | **Dirección de Origen**         | **Dirección de Origen**         |
| **Dirección de Destino**    | **Dirección de Destino**        | **Dirección de Destino**        |
| **Opciones**                | **Opciones**                    |                                |
| **Padding**                 | **Padding**                     |                                |
|                             |                                | **Flow Label** (nuevo en IPv6) |

## Leyenda

- **Campos que se mantienen**: Nombres de campos que se mantuvieron de IPv4 a IPv6.
- **Campos que no se mantienen**: Campos que no se mantienen en IPv6.
- **Campos con nombre y posición cambiados**: Campos que cambiaron de nombre y/o posición en IPv6.
- **Campo nuevo en IPv6**: Campos nuevos en IPv6.

- **Etiqueta de Flujo para QoS**

  | Bits  | Campo               | Descripción                           |
  |-------|---------------------|---------------------------------------|
  | 0 - 4 | **Versión**         | Versión del protocolo (IPv6)          |
  | 4 - 12| **Traffic Class**   | Calidad de servicio (QoS)             |
  | 12 - 32| **Flow Label**      | Manejo de flujo de paquetes           |
  | 32 - 48| **Payload Length**  | Longitud del payload                  |
  | 48 - 56| **Next Header**     | Tipo de protocolo en el payload       |
  | 56 - 64| **Hop Limit**       | Límite de saltos (TTL en IPv4)        |
  | 64 - 192| **Dirección de Origen** | Dirección de origen (128 bits)    |
  | 192 - 320| **Dirección de Destino** | Dirección de destino (128 bits) |

- **Encabezados de Extensión:**

  | Orden | Tipo de Encabezado                              | Código de Encabezado Siguiente |
  |-------|-------------------------------------------------|--------------------------------|
  | 1     | Encabezado IPv6 Básico                          | -                              |
  | 2     | Opciones Hop-by-Hop                             | 0                              |
  | 3     | Opciones de Destino (con Opciones de Enrutamiento) | 60                             |
  | 4     | Encabezado de Enrutamiento                       | 43                             |
  | 5     | Encabezado de Fragmento                          | 44                             |
  | 6     | Encabezado de Autenticación                      | 51                             |
  | 7     | Encabezado de Carga Segura de Encapsulación      | 50                             |
  | 8     | Opciones de Destino                              | 60                             |
  | 9     | Encabezado de Movilidad                          | 135                            |
  |       | Sin encabezado siguiente                        | 59                             |
  | Capa Superior | TCP                                        | 6                              |
  | Capa Superior | UDP                                        | 17                             |
  | Capa Superior | ICMPv6                                     | 58                             |

IPv6 se compone de 128 bits y su nomenclatura es hexadecimal:  
8 bloques de 16 bits

La nomenclatura de 16 bits es la siguiente: `0123456789ABCDEF`

| Hexadecimal | Decimal | Binario |
|-------------|---------|---------|
| 0           | 0       | 0000    |
| 1           | 1       | 0001    |
| 2           | 2       | 0010    |
| 3           | 3       | 0011    |
| 4           | 4       | 0100    |
| 5           | 5       | 0101    |
| 6           | 6       | 0110    |
| 7           | 7       | 0111    |
| 8           | 8       | 1000    |
| 9           | 9       | 1001    |
| A           | 10      | 1010    |
| B           | 11      | 1011    |
| C           | 12      | 1100    |
| D           | 13      | 1101    |
| E           | 14      | 1110    |
| F           | 15      | 1111    |

**Ejemplo:**

- A7F1:
  - A = 1010
  - 7 = 0111
  - F = 1111
  - 1 = 0001

- D:
  - D = 1101

## Representación

En este ejemplo se observan distintas formas de representar:

- 2001:0000:0000:0000:0000:0000:0000:0001
  - 2001:0:0:0:0:0:0:1
    - 2001::1

### Reglas:

1. Los ceros a la izquierda se pueden omitir
  - 2001:0000:0000:0000:0000:0000:0000:0001
    - 2001:0:0:0:0:0:0:1
2. Bloques en 0 se pueden representar con un único 0
  - 2001:0:0:0:0:0:0:1
3. Bloques consecutivos en 0 se pueden representar con `::`, pero solo una vez en la dirección IP
  - 2001::1

**Ejemplo 2:**

- 2001:0000:0000:1111:0000:0000:0000:0001
  - 2001:0:0:1111::1

Los dos puntos `::` irán donde hay más ceros consecutivos.

## Direccionamiento IPv6

### Tipos de direcciones:

- **UNICAST:**
  - Son el identificador de una interfaz.
        
- **ANYCAST:**
  - Son el identificador para un conjunto de interfaces; los paquetes se entregan a la dirección IP más cercana según la métrica del protocolo.
    
- **MULTICAST:**
  - Es un identificador para un conjunto de interfaces; los paquetes se entregan a todas las interfaces con esta dirección.

### **OJO YA NO HAY BROADCAST EN IPv6 Y SU FUNCIÓN ES DELEGADA A MULTICAST**

- **UNSPECIFIED ADDRESS**
  - 0:0:0:0:0:0:0:0
    - No representa ningún nodo. Puede ser utilizado al iniciar cuando el host no sabe cuál es su propia dirección.
    - No es enrutada a través de Internet.
    - No se utiliza como dirección de destino.

- **LOOPBACK ADDRESS**
  - 0:0:0:0:0:0:0:1
    - Se utiliza como dirección de destino para verificación de forma local.
    - No es enrutada a través de Internet.

- **GLOBAL ADDRESS**
  - 2000-3FFF::/3
    - Son enrutables a través de Internet.
    - Aquí se subnetea sobre las subredes; no se subneatea el host como en IPv4.

  Porque tendremos 64 bits para red y 64 bits para host.

  Aquí no se tiene que ahorrar red; esta parte es administrativa y un punto de vista de gestión.

- **LINK LOCAL**
  - Son configuradas de forma automática.
  - No son enrutables a través de Internet.

- **UNIQUE LOCAL**
  - Direccionamiento privado.

- **MULTICAST
