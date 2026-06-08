# dad-II-actividad

*Alumno:* Nicolas Fernandez Garcia

## Ejemplo 1 Captura 
<img width="998" height="473" alt="image" src="https://github.com/user-attachments/assets/8006ae46-c6fc-4912-a2f1-467ba0153d3d" />

---
## Ejemplo 2
<img width="722" height="469" alt="image" src="https://github.com/user-attachments/assets/9e9f6283-78b4-4415-8f98-fb551b82b9cd" />

---
## Ejemplo 3 

##  Inconvenientes de Ejecutar Scripts de S.O.

El script de ejem03 ilustra perfectamente los **problemas de portabilidad y compatibilidad**:

### **1. Error de Terminación de Líneas (CRLF vs LF)**
```bash
run.sh: line 2: $'\r': command not found
```
- **Causa**: El archivo fue creado en Windows (CRLF), pero bash espera LF
- **Impacto**: El script falla inmediatamente en bash
- **Solución temporal**: Convertir manualmente con herramientas como `dos2unix`

### **2. Diferencias de Rutas entre Sistemas Operativos**

| Sistema | Sintaxis | Ejemplo |
|---------|----------|---------|
| **Linux/Mac** | `$(pwd)` | `/home/user/projects/ejem03` |
| **Windows PowerShell** | `$PWD` | ejem03 |
| **Windows CMD** | `%cd%` | `D:\cosasNico\upc\DAD-II\...` |

En ejem03 usé: `source="$PWD\wordpress"` pero en Linux sería `source="$(pwd)/wordpress"`

### **3. Intérpretes de Comandos Diferentes**

El script usa `#!/bin/bash`, pero:
-  Funciona nativamente en Linux/Mac
-  En Windows requiere:
  - WSL (Windows Subsystem for Linux)
  - Git Bash
  - O traducir manualmente los comandos a PowerShell

### **4. Comandos del Sistema Incompatibles**

```bash
mkdir wordpress  # Funciona en bash, pero en PowerShell puro necesita New-Item
```

### **5. Problemas de Mantenimiento**

-  Necesitas **múltiples versiones** del mismo script:
  - run.sh para Linux/Mac
  - `run.bat` para Windows CMD
  - `run.ps1` para PowerShell
-  Mantener sincronización entre versiones es **tedioso y propenso a errores**

---

**Conclusión**: Los scripts de SO son útiles para tareas específicas del sistema, pero para **orquestación de Docker**, docker-compose es la solución estándar que elimina todos estos problemas de portabilidad. 
