# Paquetes Soportados

La Helm Pack Automation Tool actualmente soporta la creación y personalización automática de los siguientes paquetes Helm para la plataforma Palette.

## 📋 Lista de Paquetes

Los siguientes paquetes están implementados con sus correspondientes handlers:

| # | Paquete | Descripción | Repositorio |
|---|---------|-------------|-------------|
| 1 | **prometheus-operator** | Monitoreo y alertas para Kubernetes | [prometheus-community/helm-charts](https://github.com/prometheus-community/helm-charts) |
| 2 | **argo-cd** | Herramienta declarativa de entrega continua para Kubernetes | [argoproj/argo-helm](https://github.com/argoproj/argo-helm) |
| 3 | **cni-cilium** | Complemento de red que optimiza conectividad, seguridad y observabilidad | [cilium/cilium](https://github.com/cilium/cilium) |
| 4 | **aws-efs-csi** | AWS EFS CSI driver para almacenamiento de archivos | [kubernetes-sigs/aws-efs-csi-driver](https://github.com/kubernetes-sigs/aws-efs-csi-driver) |
| 5 | **external-secrets-operator** | Operador para gestionar secretos externos | [external-secrets/external-secrets](https://github.com/external-secrets/external-secrets) |
| 6 | **aws-cluster-autoscaler** | Ajusta automáticamente la cantidad de nodos en clústeres Kubernetes EKS | [kubernetes/autoscaler](https://github.com/kubernetes/autoscaler) |
| 7 | **calico-network-policy** | Políticas de red para Kubernetes | [projectcalico/calico](https://github.com/projectcalico/calico) |
| 8 | **nginx** | NGINX Ingress Controller | [kubernetes/ingress-nginx](https://github.com/kubernetes/ingress-nginx) |

## 🧩 Estructura de Handlers

Cada paquete soportado tiene su propio handler que se encarga de la personalización específica para Palette. La estructura de un handler típico incluye:

### 1. Configuración
```
src/handlers/[nombre-del-paquete]/config/config.sh
```

Aquí se definen variables importantes como:
- Nombre del paquete
- Nombre del chart
- URL del repositorio
- Directorio base
- Ruta de las plantillas

### 2. Lógica de Personalización
```
src/handlers/[nombre-del-paquete]/src/customization_pack.sh
```

Este archivo contiene las funciones que realizan las personalizaciones específicas para cada paquete, incluyendo:
- Actualización de valores en `values.yaml`
- Modificación de referencias de imágenes
- Configuración de dependencias y constraints
- Actualización de versiones en `pack.json`

### 3. Punto de Entrada 
```
src/handlers/[nombre-del-paquete]/handler.sh
```

Este archivo orquesta el proceso completo para un paquete específico:
- Descarga el chart Helm
- Verifica versiones existentes
- Copia archivos base
- Invoca las personalizaciones
- Limpia archivos temporales

### 4. Plantillas y Recursos Adicionales
```
src/handlers/[nombre-del-paquete]/templates/
```

Algunos paquetes incluyen plantillas adicionales como:
- Definiciones de constraints
- Configuraciones de StorageClass
- Otros recursos personalizados

## 🔍 Detalles y Personalizaciones

### Prometheus Operator

**Descripción**: Proporciona monitoreo y alertas para clústeres Kubernetes mediante Prometheus, Alertmanager y Grafana.

**Personalizaciones Clave**:
- Configuración de etiquetas de cluster_name para todas las métricas
- Personalización de templates para Thanos
- Actualización de URLs de imágenes para todos los componentes
- Modificación de CRDs para soportar objstoreConfig
- Configuración para alta disponibilidad

### Argo CD

**Descripción**: Herramienta declarativa de entrega continua (CD) para Kubernetes.

**Personalizaciones Clave**:
- Actualización de repositorios de imágenes para todos los componentes
- Configuración de constraints para Kubernetes
- Modificación de versiones en pack.json

### CNI Cilium

**Descripción**: Complemento de red que optimiza conectividad, seguridad y observabilidad.

**Personalizaciones Clave**:
- Actualización de repositorios de imágenes para múltiples componentes
- Personalización de constraints para compatibilidad con Kubernetes
- Configuración de recursos

### AWS EFS CSI Driver

**Descripción**: Driver CSI para usar Amazon EFS como almacenamiento persistente.

**Personalizaciones Clave**:
- Soporte para crear paquetes con o sin addon
- Configuración de StorageClass personalizada
- Actualización de repositorios de imágenes
- Personalización de constraints

### External Secrets Operator

**Descripción**: Operador para acceder a secretos externos desde Kubernetes.

**Personalizaciones Clave**:
- Actualización de valores en values.yaml
- Modificación de repositorios de imágenes
- Actualización de versiones

### AWS Cluster Autoscaler

**Descripción**: Ajusta automáticamente la cantidad de nodos en clústeres EKS.

**Personalizaciones Clave**:
- Actualización de repositorios de imágenes
- Configuración de constraints específicos para EKS
- Personalización de recursos

### Calico Network Policy

**Descripción**: Implementación de políticas de red para Kubernetes.

**Personalizaciones Clave**:
- Actualización de rutas de imágenes
- Configuración de constraints predeterminados
- Personalización del operador Tigera

### NGINX Ingress Controller

**Descripción**: Controlador de Ingress basado en NGINX.

**Personalizaciones Clave**:
- Actualización de repositorios de imágenes
- Personalización de configuración para Palette

## 🔄 Soporte para Versiones de Kubernetes

Los paquetes soportados son compatibles con las siguientes versiones de Kubernetes:

| Paquete | Versión Mínima K8s |
|---------|-------------------|
| prometheus-operator | 1.24+ |
| argo-cd | 1.27+ |
| cni-cilium | 1.27+ |
| aws-efs-csi | 1.27+ |
| external-secrets-operator | 1.24+ |
| aws-cluster-autoscaler | 1.27+ |
| calico-network-policy | 1.24+ |
| nginx | 1.24+ |

[← Volver al Índice](../README.md) | [← Anterior: Guía de Uso](usage.md) | [Siguiente: Personalización de Paquetes →](customization.md)
