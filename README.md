# Savin‑HyprChanger  
Gestor de presets seguro, modular y reversible para Hyprland.

Savin‑HyprChanger es una herramienta diseñada para usuarios de Hyprland que quieren
gestionar múltiples configuraciones (presets) de forma segura, ordenada y sin miedo
a romper nada.  
Permite crear, cambiar, restaurar y limpiar configuraciones completas de Hyprland
y aplicaciones relacionadas, todo con un sistema de backups y detección de cambios
basado en hashes.

---

## ✨ Características principales

- 📁 **Presets completos**: cada preset incluye Hyprland + Waybar + Wofi + Dunst + Kitty + Rofi + Hyprpaper + Hypridle + wallpapers + scripts.
- 🔐 **Sistema seguro**: backups automáticos, detección de cambios con SHA‑256 y carpeta `/active` como referencia del preset actual.
- 🔄 **Cambios reversibles**: puedes volver atrás en cualquier momento.
- 🧹 **Limpieza segura**: elimina tus dotfiles reales e instala una configuración básica funcional.
- ⚙️ **Autosave opcional**: guarda cambios automáticamente al cambiar de preset.
- 🧠 **Interfaz interactiva**: mensajes claros, amigables y pensados para evitar errores.

---

## 📁 Estructura de directorios

Savin‑HyprChanger crea y gestiona:

```
~/.dotpresets/
    presets/
        <preset>/
            hypr/
            apps/
    active/
        hypr/
        apps/
    backups/
        <preset>/
            hypr/
            apps/
    clear/
        hypr/
        apps/
    metadata.json
```

- **presets/** → tus presets editables  
- **active/** → copia del preset actualmente activo  
- **backups/** → versión original de cada preset  
- **clear/** → configuración básica limpia para el comando `clear`  
- **metadata.json** → estado interno del programa  

---

## 🧩 Cómo funciona

### 🔍 Detección de cambios
Cada archivo del preset activo se compara con los dotfiles reales usando **hashes SHA‑256**.  
Si hay diferencias, Savin‑HyprChanger te pregunta si quieres guardarlas.

### 🔄 Cambio de preset
1. Detecta cambios entre `/active` y los dotfiles reales.  
2. Pregunta si quieres guardarlos.  
3. Copia el nuevo preset a tu sistema.  
4. Actualiza `/active`.  
5. Recarga Hyprland o te pide reiniciar si es necesario.

### 🧹 Limpieza segura
`hyprchange clear` elimina tus dotfiles reales y los reemplaza por la configuración básica de `/clear`, manteniendo tus presets intactos.

---

## 🛠️ Comandos

### 🟦 `hyprchange create`
Crea un nuevo preset a partir de tu configuración actual.

**Mensajes:**
```
¿Quieres que guarde tus dotfiles actuales en un nuevo preset? 
(Si no, cancela con Ctrl + C)

Escribe aquí el nombre del nuevo preset (ej. "Caelestia"):
```

Si ya existe:
```
Vaya! Parece que ya existe un preset con este nombre, tendrás que elegir otro ;)
```

---

### 🟩 `hyprchange switch <preset>`
Cambia al preset indicado.

Si no existe:
```
Error: "<preset>" no existe.
Usa "hyprchange list" para ver los disponibles ;)
```

Si hay cambios:
```
Se han detectado cambios en tu configuración actual.
¿Deseas guardarlos en el preset activo?

(Si no estás seguro, te recomiendo que sí, siempre puedes volver atrás con 
 "hyprchange restore <preset>")

(S) - Sí
(N) - No
```

---

### 🟧 `hyprchange clear`
Limpia tus dotfiles reales e instala la configuración básica.

Mensaje inicial:
```
Esto eliminará todos los directorios reales de Hyprland y apps relacionadas.
No se borrarán presets, backups ni active.
¿Deseas continuar?
(S) - Sí
(N) - No
(i) - Para qué?
```

Si eliges (i):
```
Este comando da miedo, pero no te preocupes! Es totalmente seguro, te lo explico:
"hyprchange clear" borra todos tus archivos de hyprland actuales, pero hey! 
No hay de qué asustarse, savin-hyprchange conservará todos tus presets intactos.
Esto significa que puedes volver atrás simplemente eligiendo el preset que tenías 
con "hyprchange switch <preset>".

Tranquilo, trabajo para que disfrutes de hyprland al máximo de forma segura ;)
```

---

### 🟫 `hyprchange restore <preset>`
Restaura un preset desde su backup original.

Si no existe:
```
Error: Te has equivocado! Mira bien ;)
```

---

### 🟨 `hyprchange list`
Lista todos los presets y muestra el activo.

---

### 🟪 `hyprchange autosave on/off`
Activa o desactiva el guardado automático.

---

## ⚠️ Errores generales

### Directorio faltante
```
"<directorio>" no se ha encontrado, omitiendo...
```

### Permisos insuficientes
```
Error: no se pudieron modificar los archivos.
Comprueba permisos o ejecuta el comando con más privilegios.
```

---

## ❤️ Filosofía del proyecto

Savin‑HyprChanger nace para que puedas experimentar con Hyprland sin miedo.  
Cambia, rompe, prueba, juega… siempre podrás volver atrás.

---

## 📄 Licencia
*(Aquí puedes añadir MIT, GPL, etc.)*

---

Si quieres, puedo generar también:

- Un **logo ASCII** para el README  
- Una **sección de instalación**  
- Una **sección de ejemplos de uso**  
- O un **README más estilizado con emojis, badges y capturas**

Tú decides cómo quieres que luzca tu proyecto.
