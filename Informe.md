**Informe técnico: Intento de habilitación de virtualización en PC de escritorio HP y migración a WSL.**

1. Contexto inicial:  
     
- Equipo PC de escritorio HP.  
- Objetivo: Habilitar Intel Virtualization Technology (VT-x) para ejecutar una máquina virtual Ubuntu en VirtualBox con 2 CPUs y 4096 de RAM.  
- Situación: el BIOS no mostraba la opción de Virtualization Technology en el menú Advanced, a pesar de que el procesador soporta la función.  
    
    
2. Procedimiento realizado:  
- Acceso al BIOS/UEFI:  Se identificó que el BIOS del equipo no expone esta configuración.

      

      3\. Verificación en Windows

- Administrador de tareas→ Rendimiento → CPU:  
  **Virtualización: Deshabilitada.**  
- Desde CMD se utilizó el comando systeminfo  y mostró:  
  \> Extensiones de modo monitor VM: Sí (CP soporta VT-x).  
  \> Virtualización habilitada en firmware: No (BIOS la mantiene apagada).  
  \> SLAT y DEP: disponibles.  
    
3. Conclusión:   
- El procesador soporta la virtualización, pero el BIOS de la PC de escritorio HP no permite habilitarla.  
- Esto impide ejecutar máquinas virtuales de 64 bits en VirtualBox.

4. Solución implementada:  
- Se optó por instalar WSL (Windows Subsystem for Linux) mediante el comando wsl – install desde CMD abierto como administrador.  
- Tras reiniciar, se configuró Ubuntu en WSL, obteniendo un entorno Linux completo dentro de Windows sin necesidad de virtualización.  
- Se actualizaron paquetes y se instalaron herramientas de ciberseguridad básicas (nmap, wireshark, net-tools, metsplot).


5. Beneficios de la solución:  
   \> Permite practicar comandos y herramientas de Linux directamente en Windows.  
   \> Evita las limitaciones del BIOS y del hardware.  
   \> Entorno más liviano y rápido que una máquina virtual tradicional.

     

