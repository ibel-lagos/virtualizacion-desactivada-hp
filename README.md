# Informe Técnico: Intento de habilitación de virtualización en PC de escritorio HP y migración a WSL

## Contexto inicial
- **Equipo:** PC de escritorio HP  
- **Objetivo:** Habilitar Intel Virtualization Technology (VT-x) para ejecutar una máquina virtual Ubuntu en VirtualBox con 2 CPUs y 4096 MB de RAM  
- **Situación:** El BIOS no mostraba la opción de *Virtualization Technology* en el menú **Advanced**, a pesar de que el procesador soporta la función  

---

## Procedimiento realizado

### 1. Acceso al BIOS/UEFI
- Se identificó que el BIOS del equipo no expone la configuración de virtualización.

### 2. Verificación en Windows
- **Administrador de tareas → Rendimiento → CPU:**  
  - Virtualización: **Deshabilitada**  
- **CMD → `systeminfo`:**  
  - Extensiones de modo monitor VM: **Sí** (CPU soporta VT-x)  
  - Virtualización habilitada en firmware: **No** (BIOS la mantiene apagada)  
  - SLAT y DEP: **Disponibles**

---

## Conclusión
- El procesador soporta la virtualización.  
- El BIOS de la PC de escritorio HP no permite habilitarla.  
- Esto impide ejecutar máquinas virtuales de 64 bits en VirtualBox.  

---

## Solución implementada
- Instalación de **WSL (Windows Subsystem for Linux)** mediante el comando:  
  ```bash
  wsl --install
