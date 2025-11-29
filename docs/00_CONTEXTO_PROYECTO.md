# PROYECTO: NORTEBLOCK - WEB FAMILIAR

> **INSTRUCCION PARA IAs:** Este es el archivo maestro del proyecto. Leelo COMPLETO antes de hacer cualquier cambio.

---

## 📌 LECTURA RAPIDA (30 segundos)

**Que hace:** Sitio web para venta de bloques de concreto del negocio familiar Norteblock en Monsefu, Lambayeque

**Estado actual:** Version 1.0 - Web funcional publicada en Netlify

**Ultima sesion:** 2025-11-19

**Siguiente paso:** Implementar Dashboard CMS para que la familia edite contenido sin codigo

**Nivel de complejidad:** Medio-Alto (escalara a sistema completo con IA y dashboard)

---

## 🎯 CONTEXTO COMPLETO

### Proposito
Crear presencia digital profesional para Norteblock, negocio familiar de bloques de concreto, con capacidad de:
1. Mostrar productos y servicios (COMPLETADO)
2. Recibir consultas de clientes (COMPLETADO)
3. Permitir a la familia actualizar contenido sin tocar codigo (PENDIENTE)
4. Responder automaticamente preguntas frecuentes con IA (PENDIENTE)
5. Facilitar cotizaciones y pedidos (FUTURO)

### Usuario final
- **Familia Montenegro:** Propietarios del negocio, NO tienen conocimientos tecnicos
  - Necesitan editar precios, fotos, textos facilmente
  - Requieren ver pedidos/consultas que llegan
  - Deben poder agregar nuevos productos o fotos de obras

- **Clientes finales:** Constructores, maestros de obra, particulares en Monsefu
  - Necesitan informacion rapida sobre productos
  - Quieren cotizar facilmente
  - Prefieren contacto por WhatsApp

### Problema que resuelve

**FASE 1 (Actual):**
- ✅ Antes: Negocio sin presencia web, solo boca a boca
- ✅ Ahora: Web profesional publicada, accesible 24/7
- ✅ Beneficio: Clientes encuentran la empresa en Google, ven productos

**FASE 2 (En desarrollo):**
- ⏳ Antes: Juan debe actualizar codigo cada vez que cambia algo
- ⏳ Ahora: Dashboard donde familia edita sin codigo
- ⏳ Beneficio: Autonomia, actualizaciones instantaneas

**FASE 3 (Futuro):**
- 🔮 Antes: Familia debe responder manualmente todas las consultas
- 🔮 Ahora: IA responde preguntas basicas, deriva casos complejos
- 🔮 Beneficio: Ahorro de tiempo, atencion 24/7

---

## 🛠️ TECNOLOGIAS Y STACK

### Stack Actual (Fase 1 - COMPLETADO)

**Frontend:**
- HTML5
- CSS3 (diseño responsive mobile-first)
- JavaScript vanilla (sin frameworks)
- Google Fonts (Poppins)
- Font Awesome (iconos)

**Hosting:**
- Netlify (gratuito)
- GitHub (control de versiones)

**Integraciones:**
- WhatsApp Business (+51 940 267 730)

### Stack Futuro (Fase 2-3 - PLANIFICADO)

**CMS/Dashboard:**
- **Sanity.io** (Headless CMS)
  - Panel visual para familia
  - API para consumir datos en web
  - Gratis hasta 100k peticiones/mes
  - Alternativa: Strapi (si necesitamos mas control)

**Chat con IA:**
- **Chatbase** (chatbot entrenado con info de Norteblock)
  - Widget integrable en web
  - Entrenamiento con documentos
  - Gratis hasta 30 mensajes/mes
  - Alternativa: Voiceflow

**Base de Datos:**
- **Supabase** (PostgreSQL)
  - Guardar cotizaciones, consultas
  - Dashboard visual para ver datos
  - Auth si se necesita login
  - Gratis hasta 500MB

**Notificaciones:**
- Webhooks a WhatsApp cuando llega consulta
- Email notifications (opcional)

---

## 📋 ESTADO ACTUAL

### Funcionalidades completadas (Fase 1)

- [x] Landing page profesional y responsive
- [x] Seccion Hero con llamado a accion
- [x] Seccion de caracteristicas (Entrega, Calidad, Resistencia)
- [x] Catalogo de productos (Bloque de Concreto 15x20x40)
- [x] Galeria de obras (carrusel con 8 fotos)
- [x] Seccion "Sobre Nosotros" (historia familiar)
- [x] Seccion de contacto (WhatsApp, Email, Ubicacion)
- [x] Formulario de contacto que envia a WhatsApp
- [x] Boton flotante de WhatsApp
- [x] Menu responsive con hamburguesa (mobile)
- [x] Optimizacion SEO basica
- [x] Publicado en Netlify
- [x] Repositorio en GitHub

### En desarrollo (Fase 2)

- [⏳] Dashboard CMS para edicion sin codigo
- [⏳] Chat con IA integrado
- [ ] Calculadora de bloques (medidas → cantidad)
- [ ] Sistema de cotizaciones automaticas

### Pendiente (Fase 3)

- [ ] Panel de gestion de pedidos/consultas
- [ ] Blog de consejos de construccion
- [ ] Chatbot WhatsApp (ademas del de la web)
- [ ] Testimonios de clientes
- [ ] Sistema de inventario simple
- [ ] Galeria ampliable con filtros
- [ ] Dominio propio (actualmente en .netlify.app)

---

## ⚠️ REGLAS ESPECIFICAS DE ESTE PROYECTO

### CRITICAS (No negociables)

1. **Simplicidad primero:** Familia NO sabe codigo, todo debe ser visual/intuitivo
2. **Mobile-first:** Mayoría de clientes usan celular
3. **Costo cero o minimo:** Gratis hasta que negocio escale
4. **Facil de mantener:** Juan tampoco es programador avanzado
5. **NO emojis en codigo:** Windows CMD tiene problemas (regla global de Juan)

### PREFERENCIAS

1. **Dashboard visual obligatorio:** Familia debe poder editar sin llamar a Juan
2. **WhatsApp es rey:** Todo debe derivar a WhatsApp al final
3. **Imagenes reales:** Usar fotos de la fabrica/obras reales, no stock
4. **Diseño simple y limpio:** No sobrecargar, es venta de bloques (industrial)
5. **Pruebas con familia:** Validar que entienden como usar antes de lanzar

### PROHIBICIONES

1. NO usar frameworks pesados (React/Vue) - mantener vanilla JS por ahora
2. NO agregar costos mensuales sin consultar a Juan
3. NO complicar la arquitectura innecesariamente
4. NO borrar archivos sin backup
5. NO cambiar diseño drasticamente sin aprobacion familia

---

## 🗺️ ARQUITECTURA

### Estructura de directorios (Actual)

```
bloques-monsefu/
├── docs/                          ← Documentacion del proyecto (NUEVO)
│   ├── 00_CONTEXTO_PROYECTO.md   ← Este archivo
│   ├── 01_ARQUITECTURA.md         ← Arquitectura tecnica
│   ├── 02_DECISIONES.md           ← Log de decisiones
│   ├── 03_PENDIENTES.md           ← TODO list priorizado
│   └── 04_SESIONES.md             ← Registro de sesiones
├── css/
│   └── styles.css                 ← Estilos principales
├── js/
│   └── main.js                    ← JavaScript (menu, carrusel, form)
├── images/
│   ├── logo.svg                   ← Logo Norteblock
│   ├── obras/                     ← Fotos de proyectos (8 imagenes)
│   ├── bloque-concreto-apilado.jpg
│   ├── fabrica.jpg
│   └── [iconos SVG personalizados]
├── .git/                          ← Control de versiones
├── .gitignore
├── index.html                     ← Pagina principal
├── CHANGELOG.md                   ← Registro de cambios
├── SESIONES.md                    ← Plan de sesiones (migrar a docs/)
└── README - copia.md              ← README antiguo
```

### Estructura futura (Fase 2)

```
bloques-monsefu/
├── docs/                          ← Documentacion
├── public/                        ← Frontend estatico (NUEVO)
│   ├── index.html
│   ├── css/
│   ├── js/
│   └── images/
├── sanity-studio/                 ← CMS Dashboard (NUEVO)
│   ├── schemas/                   ← Modelos de datos
│   │   ├── producto.js
│   │   ├── obra.js
│   │   └── configuracion.js
│   └── sanity.config.js
├── functions/                     ← Serverless functions (NUEVO)
│   ├── cotizacion.js              ← Generar cotizaciones
│   └── notificar-whatsapp.js      ← Enviar notificaciones
└── chatbot/                       ← Configuracion IA (NUEVO)
    ├── entrenamiento.txt          ← Info para entrenar bot
    └── config.json
```

### Flujo principal (Actual)

```
Cliente visita web
    ↓
Ve productos, galeria, info
    ↓
Decide contactar
    ↓
Opcion 1: Click boton WhatsApp → Abre chat directo
Opcion 2: Llena formulario → Envia mensaje WhatsApp automatico
    ↓
Familia responde manualmente por WhatsApp
```

### Flujo futuro (Fase 2-3)

```
Cliente visita web
    ↓
Ve contenido (editado por familia via Dashboard)
    ↓
Tiene duda → Chat IA responde instantaneamente
    ↓
Pregunta compleja → IA deriva a WhatsApp con contexto
    ↓
Familia ve consulta en Panel de Gestion
    ↓
Responde con contexto completo
```

---

## 📂 MAPA DE ARCHIVOS CRITICOS

### `index.html` (389 lineas)

**Que hace:** Pagina principal del sitio

**Secciones importantes:**
- Lineas 1-27: Metadata y SEO (Open Graph, keywords)
- Lineas 30-59: Header/Navegacion
- Lineas 62-84: Hero section (principal)
- Lineas 87-115: Caracteristicas (3 cards)
- Lineas 118-150: Productos (solo 1 por ahora)
- Lineas 153-210: Galeria de obras (carrusel)
- Lineas 213-254: Sobre Nosotros
- Lineas 257-325: Contacto (form + info cards)
- Lineas 328-375: Footer
- Linea 73-76: WhatsApp link principal (+51 940 267 730)

**Dependencias:**
- css/styles.css
- js/main.js
- images/ (logo, productos, obras)

### `css/styles.css`

**Que hace:** Todos los estilos del sitio

**Secciones importantes:**
- Variables CSS (colores, fuentes)
- Reset y base styles
- Header y navegacion
- Hero section
- Componentes reutilizables (cards, botones)
- Carrusel de obras
- Media queries (responsive)

**Puntos criticos:**
- Mobile-first approach
- Breakpoints: 768px (tablet), 1024px (desktop)

### `js/main.js`

**Que hace:** Interactividad del sitio

**Funciones principales:**
- toggleMenu(): Menu hamburguesa mobile
- carouselControls(): Navegacion carrusel
- smoothScroll(): Scroll suave entre secciones
- formSubmit(): Envio a WhatsApp desde formulario
- activeNavLink(): Resalta seccion actual en menu

**Puntos criticos:**
- Vanilla JS, sin dependencias
- Compatible IE11+ (por si acaso)

### `SESIONES.md` (actual)

**Que hace:** Plan de trabajo por sesiones

**Contenido:**
- Sesion 1 completada (2025-11-19)
- Sesiones 2-5 planificadas (chatbot, ajustes)
- Metricas de exito

**NOTA:** Este archivo sera migrado a `docs/04_SESIONES.md` con formato mejorado

---

## 🔧 CONFIGURACION

### Variables importantes

**WhatsApp:**
- Numero: +51 940 267 730
- Usado en: Boton flotante, formulario, tarjetas de contacto

**Email:**
- Actual: contacto@norteblock.com (placeholder, verificar si existe)

**Ubicacion:**
- Ciudad de Monsefu a 11 KM de Chiclayo, Lambayeque, Peru

**Redes sociales:**
- Ninguna configurada aun

### URLs de produccion

- **Repositorio GitHub:** https://github.com/JKarlos2025IA/norteblock-web.git
- **Usuario GitHub:** JKarlos2025IA
- **Web Netlify:** [URL de Netlify - verificar en dashboard]

### Git workflow

```cmd
# Ver estado
git status

# Guardar cambios (SIEMPRE hacer esto)
git add .
git commit -m "Descripcion del cambio"
git push origin main

# IMPORTANTE: Push activa deploy automatico en Netlify
```

**PROTOCOLO CRITICO:** SIEMPRE hacer git push para evitar perder trabajo

---

## 🚀 COMO EJECUTAR

### Ver web localmente

```cmd
# Opcion 1: Doble click en index.html

# Opcion 2: Servidor local
cd C:\Users\juan.montenegro\Desktop\bloques-monsefu
python -m http.server 8000
# Abrir: http://localhost:8000
```

### Hacer cambios y publicar

```cmd
# 1. Hacer cambios en archivos
# 2. Probar localmente
# 3. Commit y push
git add .
git commit -m "Descripcion del cambio"
git push origin main

# 4. Netlify detecta cambios y publica automaticamente
```

---

## 📝 HISTORIAL DE SESIONES

### 2025-11-19 - Sesion 1 (COMPLETADA)
**Duracion:** 45 minutos
**Objetivo:** Publicar web inicial con galeria de obras

**Completado:**
- [x] Carrusel de obras con 8 fotos
- [x] Actualizacion de textos (cemento, medidas, Monsefu)
- [x] Simplificacion productos (solo Bloque Concreto)
- [x] Publicacion en Netlify
- [x] Configuracion GitHub

**Archivos modificados:**
- index.html (carrusel + textos)
- css/styles.css (estilos carrusel)
- js/main.js (funcionalidad carrusel)
- images/obras/ (8 fotos agregadas)

**Pendiente:**
- Cambiar email de contacto si es necesario
- Optimizacion SEO avanzada
- Pruebas con familia

### 2025-01-28 - Sesion 2 (HOY - Documentacion)
**Duracion:** En curso
**Objetivo:** Crear sistema de documentacion completo

**Completado:**
- [x] Analisis del proyecto existente
- [x] Cuestionario de contexto
- [x] Creacion de carpeta docs/
- [x] Archivo 00_CONTEXTO_PROYECTO.md (este archivo)
- [⏳] Pendiente: 01_ARQUITECTURA.md
- [⏳] Pendiente: 02_DECISIONES.md
- [⏳] Pendiente: 03_PENDIENTES.md
- [⏳] Pendiente: 04_SESIONES.md

**Siguiente paso:**
- Completar documentacion
- Planificar Fase 2 (Dashboard + IA)

---

## 🐛 PROBLEMAS CONOCIDOS

### Problema 1: Email placeholder
**Sintoma:** contacto@norteblock.com puede no existir
**Causa:** No se verifico si email esta activo
**Workaround:** Clientes usan WhatsApp principalmente
**Solucion definitiva:** Verificar email real o quitar seccion

### Problema 2: Imagenes no optimizadas
**Sintoma:** Algunas fotos pueden ser pesadas
**Causa:** Fotos directas de celular sin compresion
**Workaround:** Netlify tiene CDN que ayuda
**Solucion definitiva:** Comprimir imagenes con TinyPNG

### Problema 3: Solo 1 producto
**Sintoma:** Seccion productos tiene solo 1 item
**Causa:** Por ahora solo venden bloques estandar
**Workaround:** Diseño funciona con 1 producto
**Solucion definitiva:** Agregar mas productos cuando ofrezcan variedad

---

## 💡 DECISIONES TECNICAS IMPORTANTES

> **Nota:** Para decisiones detalladas ver `02_DECISIONES.md`

### Decision 1: Vanilla JS sin frameworks
**Fecha:** 2025-11 (inicio proyecto)
**Que se decidio:** No usar React/Vue/Angular
**Por que:** Simplicidad, Juan no es programador avanzado, site es simple
**Ver:** 02_DECISIONES.md#decision-1

### Decision 2: Netlify como hosting
**Fecha:** 2025-11-19
**Que se decidio:** Netlify en vez de hosting tradicional
**Por que:** Gratis, deploys automaticos, rapido
**Ver:** 02_DECISIONES.md#decision-2

### Decision 3: Sanity para CMS futuro
**Fecha:** 2025-01-28 (planificacion)
**Que se decidio:** Sanity.io como dashboard para familia
**Por que:** Visual, facil, gratis tier generoso, mejor que Strapi para no-tecnicos
**Ver:** 02_DECISIONES.md#decision-3

---

## 🎓 RECURSOS Y REFERENCIAS

**Documentacion oficial:**
- [Netlify Docs](https://docs.netlify.com/)
- [Sanity.io Docs](https://www.sanity.io/docs)
- [Chatbase Docs](https://www.chatbase.co/docs)

**Referencias internas:**
- G:\Mi unidad\03_PROJECTS\0000_MEMORY\01_REGLAS_EFICIENCIA.md
- G:\Mi unidad\03_PROJECTS\0000_MEMORY\02_PROTOCOLO_PROYECTOS.md

**Recursos de diseño:**
- Google Fonts - Poppins
- Font Awesome - Iconos
- Coolors.co - Paleta de colores

---

## 📞 CONTACTO Y EQUIPO

**Desarrollador:** Juan Montenegro (con ayuda de IAs)
**Propietarios:** Familia Montenegro
**Negocio:** Norteblock - Bloques de concreto
**Ubicacion:** Monsefu, Lambayeque, Peru
**WhatsApp Negocio:** +51 940 267 730

---

## 🔄 CONTROL DE VERSIONES

**Version actual:** 1.0 (Web funcional publicada)
**Ultima actualizacion:** 2025-01-28
**Actualizado por:** Claude (Anthropic)

### Changelog

- **v1.0** (2025-11-19): Web inicial publicada, carrusel obras, Netlify deploy
- **v1.1** (2025-01-28): Sistema de documentacion completo, planificacion Fase 2

---

## 📌 NOTAS PARA PROXIMA SESION

- [ ] Completar archivos de documentacion (01-04)
- [ ] Decidir entre Sanity vs Strapi para CMS
- [ ] Investigar Chatbase vs Voiceflow para IA
- [ ] Diseñar estructura de datos para Dashboard
- [ ] Crear mockups de como familia usara Dashboard
- [ ] Validar que email contacto@norteblock.com existe
- [ ] Considerar comprimir imagenes de obras

---

**Fin del archivo de contexto**
