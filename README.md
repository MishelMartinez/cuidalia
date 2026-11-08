# CuidalIA · Prototipo navegable de alta fidelidad

> Del reconocimiento de experiencias al empleo en cuidado infantil.

## Descripción

CuidalIA es un prototipo interactivo de alta fidelidad que simula una aplicación móvil real para mujeres cuidadoras. Traduce la experiencia de cuidado familiar en competencias formales y conecta a las usuarias con oportunidades laborales en el sector del cuidado infantil.

**Archivo único:** `index.html` · Sin dependencias externas · Funciona sin Internet.

---

## Ejecución local

1. Descarga o clona este repositorio.
2. Abre `index.html` directamente en cualquier navegador moderno.
   - Chrome 90+, Firefox 88+, Safari 14+, Edge 90+.
3. No requiere servidor, instalación ni conexión a Internet.

```bash
# Opción alternativa con servidor local (para evitar restricciones CORS)
npx serve .
# o
python3 -m http.server 8080
```

---

## Publicación en GitHub Pages

```bash
# 1. Crea un repositorio en GitHub
# 2. Sube el archivo index.html a la rama main
git init
git add index.html
git commit -m "feat: prototipo CuidalIA v1.0"
git branch -M main
git remote add origin https://github.com/tu-usuario/cuidalia.git
git push -u origin main

# 3. En GitHub → Settings → Pages → Source: Deploy from branch → main → / (root)
# 4. Tu prototipo estará en: https://tu-usuario.github.io/cuidalia/
```

---

## Pantallas implementadas

| # | Pantalla | Función |
|---|----------|---------|
| 01 | Bienvenida | Splash de la app, propuesta de valor, acceso a demo rápida |
| 02 | Registro y privacidad | Formulario con validación, consentimiento de datos |
| 03 | Bienvenida personalizada | Saludo con nombre, presentación del flujo |
| 03b | Disponibilidad previa | Zona y horas (paso opcional previo a entrevista) |
| 04 | Preparación de entrevista | Información sobre la entrevista de IA, opciones de modo |
| 05 | Entrevista en vivo | Chat interactivo con preguntas guiadas (5 turnos), opciones predefinidas y texto libre |
| 06 | Revisión de experiencias | Muestra las experiencias identificadas con etiquetas |
| 07 | Traductor de habilidades | Animación de procesamiento + gráficas de barras con 8 habilidades |
| 08 | Validación de habilidades | Selección múltiple, activa el botón al seleccionar |
| 09 | Pasaporte de Talento | Tarjeta profesional con habilidades, estadísticas y compartir |
| 10 | Mi disponibilidad | Zona, horas (slider), días de la semana, modalidad |
| 11 | Orientación profesional | Grid de 6 áreas de interés seleccionables |
| 12 | Objetivo: cuidado infantil | 4 roles con selección única |
| 13 | Fortalezas y brechas | Diagnóstico con barras de progreso en dos secciones |
| 14 | Cursos recomendados | 4 tarjetas con institución, duración, certificación y costo |
| 15 | ¿Deseas capacitarte? | Bifurcación: Ruta de aprendizaje vs Oportunidades directas |
| 16 | Mi ruta de aprendizaje | Timeline de 3 módulos con estados |
| 17 | Oportunidades DEMO | 5 vacantes con match%, filtros por categoría, filtros avanzados |
| 18 | Postulación DEMO | Detalle de vacante + envío simulado |
| 19 | Seguimiento | Historial de postulaciones con estados |
| — | Mi perfil | Datos del usuario, accesos rápidos, reset de demo |

**Total: 21 pantallas** (19 del flujo principal + Perfil + Demo rápida)

---

## Flujos implementados

### Flujo principal completo
```
Bienvenida → Registro → Bienvenida personal → Disponibilidad previa →
Prep. entrevista → Entrevista (5 preguntas) → Revisión →
Traductor (con animación) → Validación → Pasaporte →
Disponibilidad → Orientación → Objetivo → Fortalezas/Brechas →
Cursos → Capacitación → [Ruta] → Oportunidades → Postulación → Seguimiento
```

### Demo rápida
Botón en la pantalla de bienvenida que carga un perfil pre-configurado y lleva directamente a Oportunidades.

### Navegación libre (después del Pasaporte)
Barra inferior con 5 destinos: Inicio · Mi ruta · Pasaporte · Empleos · Perfil

---

## Funciones reales, simuladas y pendientes

### Reales (funcionan en el prototipo)
- ✅ Formulario de registro con validación de campos, correo y longitud de contraseña
- ✅ Persistencia con `localStorage` (el progreso se conserva al recargar)
- ✅ Entrevista interactiva con 5 preguntas y opciones + texto libre
- ✅ Selección y validación de habilidades
- ✅ Filtrado de vacantes por categoría
- ✅ Historial de postulaciones (sesión)
- ✅ Reset completo de la demostración

### Simuladas (datos de demostración)
- 🔶 Procesamiento de IA (respuestas y traducciones son datos precargados)
- 🔶 Vacantes laborales (datos ficticios, no integración real)
- 🔶 Postulación (no envía información a ningún servidor)
- 🔶 Seguimiento de postulaciones (no hay notificaciones reales)
- 🔶 Cursos e instituciones (ejemplos de validación UX)
- 🔶 Entrevista por voz (simulada con texto)
- 🔶 Compartir Pasaporte (toast de confirmación, sin enlace real)

### Pendientes de integración (fuera del scope del prototipo)
- ⏳ Backend de autenticación real
- ⏳ Motor de IA para procesamiento de voz y texto
- ⏳ Integración con bolsas de trabajo reales
- ⏳ Sistema de notificaciones push
- ⏳ API de instituciones educativas
- ⏳ Base de datos de usuarias y pasaportes

---

## Paleta de colores

| Token | Hex | Uso |
|-------|-----|-----|
| `--mint` | `#5BA8A2` | Color primario, CTAs, progreso |
| `--mint-dark` | `#3D8A84` | Énfasis, hover states |
| `--lilac` | `#9B7BB8` | Acento secundario, IA |
| `--clay` | `#B8866A` | Advertencias, elementos terciarios |
| `--olive` | `#8FAA5E` | Éxito, elementos positivos |
| `--ink` | `#1E3340` | Texto principal |

---

## Arquitectura técnica

- **Un solo archivo** HTML con CSS y JS inline
- **Sin dependencias externas** (cero CDN, cero npm)
- **Estado central** en objeto JavaScript + `localStorage`
- **Sistema de pantallas** con CSS transitions (slide in/out)
- **Mobile First** con max-width 440px en desktop
- **Accesibilidad**: `aria-label`, `aria-hidden`, `focus-visible`, `prefers-reduced-motion`

---

*Prototipo de validación UX · CuidalIA v1.0 · Noviembre 2026*
