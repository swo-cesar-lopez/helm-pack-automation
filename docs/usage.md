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
