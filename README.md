# Informe Técnico: Intento de habilitación de virtualización en PC de escritorio HP y migración a WSL

## Contexto inicial
- Equipo: PC de escritorio HP con sistema operativo Windows 10 (64 bits).
- *Objetivo:* Habilitar Intel Virtualization Technology (VT-x) para ejecutar una máquina virtual Ubuntu en VirtualBox con 2 CPUs y 4096 MB de RAM  
- *Situación:* El BIOS no mostraba la opción de Virtualization Technology en el menú Advanced, a pesar de que el procesador soporta la función  

---

## Procedimiento realizado

### 1. Acceso al BIOS/UEFI
- Se identificó que el BIOS del equipo no expone la configuración de virtualización.  

### 2. Verificación en Windows
- *Administrador de tareas → Rendimiento → CPU:*  
  - Virtualización: Deshabilitada  
- *CMD → systeminfo:*  
  - Extensiones de modo monitor VM: Sí (CPU soporta VT-x)  
  - Virtualización habilitada en firmware: No (BIOS la mantiene apagada)  
  - SLAT y DEP: Disponibles  

---

## Solución implementada
- Instalación de WSL (Windows Subsystem for Linux) mediante el comando:  
  ```bash
  wsl --install

La instalación de WSL permitió continuar con prácticas básicas en Linux, pero no resolvió la limitación original: no fue posible ejecutar máquinas virtuales de 64 bits en VirtualBox debido a la falta de soporte de virtualización en el BIOS. Se realizaron múltiples intentos en PowerShell para habilitar la virtualización, sin éxito, confirmando que la restricción proviene del firmware.

## Conclusión
- El procesador soporta la virtualización.  
- El BIOS de la PC de escritorio HP no permite habilitarla.  
- Esto impide ejecutar máquinas virtuales de 64 bits en VirtualBox.  

---

## Lecciones aprendidas
- Verificar compatibilidad de BIOS/UEFI antes de planear un laboratorio con máquinas virtuales.  
- El soporte del procesador no garantiza que el firmware exponga las opciones necesarias.  
- Documentar limitaciones es tan importante como documentar éxitos: aporta claridad y evita repetir errores.  


## Alternativas evaluadas
- VirtualBox: descartado por falta de VT-x habilitable.  
- WSL: implementado como solución parcial para continuar con prácticas básicas.  
- Dual boot con Ubuntu: considerado como solución definitiva para superar la restricción.  



## Impacto en el proyecto
- Limitación: no se pudieron usar máquinas virtuales de 64 bits en este equipo.  
- Mitigación: migración a WSL para continuar con prácticas iniciales.  
- Próximo paso: instalación nativa de Ubuntu en otra PC para disponer de un entorno completo.  


## Recomendaciones futuras 
- Al elegir hardware para proyectos de virtualización, confirmar que la BIOS permita habilitar VT-x/AMD-V.  
- Priorizar equipos con BIOS/UEFI modernos y configurables.  
- Mantener informes técnicos incluso cuando el resultado no sea exitoso: reflejan capacidad de análisis y adaptación.
- Instalación de WSL (Windows Subsystem for Linux) mediante el comando:  
  ```bash
  wsl --install
