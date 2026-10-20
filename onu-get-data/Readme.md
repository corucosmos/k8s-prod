## 🚀 Requisitos Previos

Asegúrate de tener instalados y configurados los siguientes componentes en el sistema Debian:

1. **K3s**: Instancia de Kubernetes ligera en ejecución.
2. **Kubectl**: Configurado mediante `$HOME/.kube/config` (apuntando a `/etc/rancher/k3s/k3s.yaml`).
3. **Privilegios de sudo**: Requeridos para importar imágenes directamente al runtime `containerd` de K3s (`k3s ctr`).
4. **Helm** Gestor de paquetes oficial para Kubernetes, para Sealed Secrets
5. **Sealed Secrets** Controlador en el clúster Kubernetes, almacena credenciales cifradas
6. **kubeseal** Herramienta CLI de cliente utilizada en tu máquina local para cifrar secretos

---

## ⚙️ Configuración y Despliegue

### 1. Definición de Credenciales (`k8s/sealed-secrets.yaml`) para depligue en PROD
Antes de iniciar el despliegue, asegúrate de configurar tus credenciales y secretos en SealedSecret dentro del archivo `k8s/sealed-secret.yml`:

### 2. Ejecución del Despliegue Automatizado
El repositorio incluye un flujo de trabajo automatizado en .github/workflows/onu-get-data.yml que se encarga de empaquetar, transferir y desplegar la aplicación en tu clúster K3s de producción ante cada TAG en el repositorio de la App.
