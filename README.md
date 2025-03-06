# Helm Pack Automation Tool

La Helm Pack Automation Tool es una herramienta de línea de comandos diseñada para automatizar la creación, actualización y personalización de paquetes Helm para la plataforma Palette de Spectro Cloud. Esta herramienta simplifica el proceso de mantenimiento de paquetes Helm, asegurando que sigan un estándar consistente y contengan todas las personalizaciones necesarias para funcionar correctamente en Palette.

## 🚀 Características Principales

- **Automatización Completa**: Crea y actualiza paquetes Helm con todas las personalizaciones necesarias
- **Interfaz Amigable**: Menú interactivo para seleccionar paquetes y versiones
- **Soporte para Múltiples Paquetes**: Compatible con una amplia gama de paquetes populares
- **Personalización Flexible**: Aplica automáticamente las personalizaciones específicas de Palette
- **Arquitectura Modular**: Fácilmente extensible para añadir soporte para nuevos paquetes

## 📋 Índice de Documentación

- [Introducción y Visión General](docs/introduction.md)
- *(In progress)* [Arquitectura del Sistema](docs/architecture.md)
- *(Pending)* [Requisitos e Instalación](docs/installation.md)
- *(In progress)* [Guía de Uso](docs/usage.md)
- *(Pending)* [Paquetes Soportados](docs/supported-packages.md)
- *(Pending)* [Personalización de Paquetes](docs/customization.md)
- *(Pending)* [Desarrollo y Extensión](docs/development.md)
- *(Pending)* [Solución de Problemas](docs/troubleshooting.md)
- *(Pending)* [Contribución al Proyecto](docs/contributing.md)

## 🚀 Inicio Rápido

```bash
# Clonar el repositorio
git clone https://github.com/swo-cesar-lopez/helm-pack-automation.git

# Navegar al directorio
cd helm-pack-automation

# Configurar la ubicación base de los paquetes (opcional)
export LOCAL_PATH="/ruta/a/tus/paquetes"

# Ejecutar la herramienta
./src/main.sh
```

## 🧰 Paquetes Actualmente Soportados

- Argo CD
- AWS Cluster Autoscaler
- AWS EFS CSI
- Calico Network Policy
- CNI Cilium
- External Secrets Operator
- NGINX
- Prometheus Operator

## 📝 Licencia

Este proyecto está licenciado bajo [INCLUIR LICENCIA]

## 🤝 Contribución

Las contribuciones son bienvenidas. Por favor, lee la [guía de contribución](docs/contributing.md) para más detalles.
