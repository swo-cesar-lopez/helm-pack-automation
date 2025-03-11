# Guía de Uso

## 🚀 Iniciar la Herramienta

Para iniciar la Helm Pack Automation Tool, ejecuta el script principal:

```bash
./src/main.sh
```

Verás el menú principal con la lista de paquetes disponibles:

```
═══════════════════════════════════════════════════════════════════════════
                        Helm Pack Creator Tool
═══════════════════════════════════════════════════════════════════════════

Available Packages:
═══════════════════════════════════════════════════════════════════════════
No. Package                             Description
═══════════════════════════════════════════════════════════════════════════
1   prometheus-operator                 Monitoreo y alertas para Kubernetes
2   argo-cd                             Herramienta declarativa de entrega continua (CD) para Kubernetes
3   cni-cilium                          Complemento de red optimiza conectividad, seguridad y observabilidad
...
0) Exit
```

## 📋 Interfaz de Línea de Comandos

### Menú Principal

El menú principal muestra todos los paquetes soportados. Para seleccionar un paquete, ingresa el número correspondiente y presiona Enter.

### Selección de Versión

Después de seleccionar un paquete, se mostrará el menú de selección de versión:

```
═══════════════════════════════════════════════════════════════════════════
Version Selection for Package: prometheus-operator
═══════════════════════════════════════════════════════════════════════════

1) Use latest version
2) Specify version

═══════════════════════════════════════════════════════════════════════════
```

- **Opción 1**: Usar la última versión disponible en el repositorio
- **Opción 2**: Especificar una versión concreta (en formato X.Y.Z)

### Resumen y Confirmación

Después de seleccionar la versión, se mostrará un resumen de la operación:

```
═══════════════════════════════════════════════════════════════════════════
Package Selection Summary
═══════════════════════════════════════════════════════════════════════════

Selected Package: prometheus-operator
Version:         45.27.2

═══════════════════════════════════════════════════════════════════════════

Do you want to proceed? (y/N):
```

Ingresa `y` para continuar o `n` para cancelar.

### Proceso de Creación

Durante el proceso de creación, la herramienta mostrará información sobre las acciones que está realizando:

```
⚡ [INFO] Adding/Updating Helm repository: kube-prometheus-stack
⚡ [INFO] Download Latest Chart...
⚡ [INFO] Copying base files...
⚡ [INFO] ✓ Copy: logo.png
⚡ [INFO] ✓ Copy: pack.json
...
⚡ [INFO] Updating kube-prometheus-stack values.yaml with latest values...
⚡ [INFO] Updating kube-prometheus-stack thanos-ruler folder changes with latest values...
...
⚡ [SUCCESS] kube-prometheus-stack Chart Version: 45.27.2 App Version: 0.63.0 pack created successfully.
⚡ [SUCCESS] Location> /ruta/a/tus/paquetes/prometheus-operator-45.27.2

Create another package? (y/N):
```

## 🔄 Flujo de Trabajo Típico

### 1. Crear un Nuevo Paquete

Para crear un nuevo paquete:

1. Inicia la herramienta: `./src/main.sh`
2. Selecciona el paquete deseado del menú
3. Elige usar la última versión o especifica una versión concreta
4. Revisa el resumen y confirma la operación
5. Espera a que la herramienta complete el proceso

El paquete creado estará disponible en la ruta configurada en `LOCAL_PATH`.

### 2. Actualizar un Paquete Existente

El proceso para actualizar un paquete es el mismo que para crear uno nuevo. La herramienta verificará si ya existe un paquete con la versión solicitada y, si es así, te informará para evitar duplicados.

## 🧩 Casos de Uso Comunes

### Crear un Paquete con la Última Versión

```bash
# Iniciar la herramienta
./src/main.sh

# En el menú principal, seleccionar un paquete (por ejemplo, 1 para prometheus-operator)
# En el menú de versiones, seleccionar 1 para usar la última versión
# Confirmar la operación
```

### Crear un Paquete con una Versión Específica

```bash
# Iniciar la herramienta
./src/main.sh

# En el menú principal, seleccionar un paquete
# En el menú de versiones, seleccionar 2 para especificar versión
# Ingresar la versión específica (por ejemplo, 45.27.2)
# Confirmar la operación
```

### Crear un Paquete AWS EFS CSI como Addon

Algunos paquetes, como AWS EFS CSI, tienen opciones adicionales:

```bash
# Iniciar la herramienta
./src/main.sh

# Seleccionar la opción para AWS EFS CSI
# Seleccionar la versión deseada
# Cuando se pregunte "Is this an addon pack?", responder "yes" para crear un paquete addon
```

## 🔧 Opciones Avanzadas

### Variables de Entorno

La herramienta reconoce varias variables de entorno para personalizar su comportamiento:

```bash
# Ruta base donde se encuentran/crearán los paquetes
export LOCAL_PATH="/ruta/a/tus/paquetes"

# Modo de depuración
export DEBUG=true

# Dirección de un proxy (si es necesario)
export HTTP_PROXY="http://tu-proxy:puerto"
export HTTPS_PROXY="http://tu-proxy:puerto"
```

### Activar Modo Debug

Para obtener información más detallada durante la ejecución, puedes activar el modo debug:

```bash
# Activar modo de depuración para obtener más información
DEBUG=true ./src/main.sh
```

Esto mostrará mensajes de depuración adicionales que normalmente están ocultos, lo que puede ser útil para solucionar problemas.

## 📊 Ejemplos de Salida

### Ejemplo: Creación Exitosa de Paquete

```
⚡ [INFO] Adding/Updating Helm repository: argo-cd
⚡ [INFO] Download Latest Chart...
⚡ [INFO] Copying base files...
⚡ [INFO] ✓ Copy: logo.png
⚡ [INFO] ✓ Copy: pack.json
⚡ [INFO] ✓ Copy: presets.yaml
⚡ [INFO] ✓ Copy: README.md
⚡ [INFO] ✓ Copy: values.yaml
⚡ [INFO] Updating argo-cd section in values.yaml with latest values...
⚡ [INFO] Updating argo-cd section in pack.json with latest values...
⚡ [SUCCESS] argo-cd Chart Version: 5.35.1 App Version: 2.8.0 pack created successfully.
⚡ [SUCCESS] Location> /ruta/a/tus/paquetes/argocd-5.35.1
```

### Ejemplo: Paquete Ya Existente

```
⚡ [INFO] Adding/Updating Helm repository: kube-prometheus-stack
⚡ [INFO] Download Chart Version: 45.27.2...
⚡ [WARNING] The pack is already up-to-date with version 45.27.2.
⚡ [WARNING] No changes are needed.
```

### Ejemplo: Error por Dependencia Faltante

```
⚡ [ERROR] Command 'yq' not found or not executable.
⚡ [ERROR] Please install yq to continue. You can find installation instructions at: https://github.com/mikefarah/yq#install
```

## 🔍 Indicadores y Mensajes

La herramienta utiliza un sistema de logging con colores y prefijos para facilitar la interpretación de los mensajes:

- **⚡ [INFO]**: Información sobre el proceso (azul)
- **⚡ [SUCCESS]**: Operación completada con éxito (verde)
- **⚡ [WARNING]**: Advertencias que no detienen el proceso (amarillo)
- **⚡ [ERROR]**: Errores que impiden continuar (rojo)
- **[DEBUG]**: Información detallada para depuración (cian, solo visible con DEBUG=true)

[← Volver al Índice](../README.md) | [← Anterior: Instalación](installation.md) | [Siguiente: Paquetes Soportados →](supported-packages.md)
