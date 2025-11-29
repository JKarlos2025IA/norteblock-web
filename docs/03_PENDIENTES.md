# PENDIENTES - Norteblock Web

**Proyecto:** Norteblock - Sitio Web Familiar
**Version:** 1.0 → 2.0+
**Ultima actualizacion:** 2025-01-28

---

## 📋 COMO USAR ESTE ARCHIVO

Este archivo es el roadmap oficial del proyecto.

**Reglas:**
1. Organizado por fases (Fase 1 completada, Fase 2-4 futuras)
2. Cada tarea tiene prioridad (P0 = critico, P1 = importante, P2 = deseado, P3 = futuro)
3. Estimaciones de tiempo incluidas
4. Actualizar al completar tareas
5. NO borrar completados, mantener historial

**Estados:**
- [x] Completado
- [⏳] En progreso
- [ ] Pendiente
- [❌] Cancelado/Bloqueado

---

## ✅ FASE 1: WEB BASICA (COMPLETADA)

**Objetivo:** Presencia digital profesional
**Plazo:** 2025-11-19
**Estado:** ✅ 100% Completado

### Funcionalidades completadas

- [x] **2025-11-19:** Landing page responsive
- [x] **2025-11-19:** Seccion hero con CTA
- [x] **2025-11-19:** Seccion caracteristicas (3 cards)
- [x] **2025-11-19:** Catalogo de productos (1 producto)
- [x] **2025-11-19:** Galeria de obras (carrusel 8 fotos)
- [x] **2025-11-19:** Seccion "Sobre Nosotros"
- [x] **2025-11-19:** Seccion contacto con formulario
- [x] **2025-11-19:** Boton flotante WhatsApp
- [x] **2025-11-19:** Menu responsive (hamburguesa mobile)
- [x] **2025-11-19:** Publicacion en Netlify
- [x] **2025-11-19:** Repositorio GitHub
- [x] **2025-01-28:** Sistema de documentacion completo

**Resultado:** Web funcional publicada, familia puede compartir link

---

## 🚀 FASE 2: AUTONOMIA FAMILIAR (En planificacion)

**Objetivo:** Familia edita contenido sin codigo + IA responde consultas
**Plazo estimado:** 2-4 semanas
**Estado:** 📋 Planificada

### 🔥 P0: Critico (Base del sistema)

#### Dashboard CMS (Sanity)

- [ ] **Configurar proyecto Sanity**
  - Contexto: Familia necesita editar productos, fotos, textos sin codigo
  - Accion: Crear proyecto, definir schemas (producto, obra, config)
  - Estimacion: 2 horas
  - Archivos: sanity-studio/ (nuevo)
  - Documentacion: [Sanity docs](https://www.sanity.io/docs)

- [ ] **Definir schemas de datos**
  - Contexto: Estructura de productos, obras, configuracion
  - Accion: Crear schemas en Sanity Studio
  - Estimacion: 2 horas
  - Archivos: sanity-studio/schemas/producto.js, obra.js, configuracion.js
  - Dependencia: Proyecto Sanity creado

- [ ] **Migrar contenido actual a Sanity**
  - Contexto: Contenido hardcodeado en HTML → Sanity
  - Accion: Copiar productos, obras actuales a Sanity
  - Estimacion: 1 hora
  - Archivos: Datos en Sanity CMS
  - Dependencia: Schemas definidos

- [ ] **Conectar web a Sanity API**
  - Contexto: Frontend debe consumir datos desde Sanity
  - Accion: Crear sanity-client.js, fetch productos/obras
  - Estimacion: 3 horas
  - Archivos: js/sanity-client.js (nuevo)
  - Dependencia: Contenido migrado

- [ ] **Probar cambios Sanity → Web**
  - Contexto: Verificar que edicion en Sanity aparece en web
  - Accion: Cambiar producto en Sanity, verificar en web
  - Estimacion: 30 min
  - Dependencia: Web conectada a Sanity

### ⚡ P1: Importante (Valor inmediato)

#### Chat IA

- [ ] **Configurar Chatbase**
  - Contexto: IA para responder preguntas frecuentes
  - Accion: Crear cuenta, configurar bot
  - Estimacion: 1 hora
  - Herramienta: [Chatbase](https://www.chatbase.co/)

- [ ] **Entrenar bot con info Norteblock**
  - Contexto: Bot debe conocer productos, precios, ubicacion
  - Accion: Subir documento con info, probar conversaciones
  - Estimacion: 2 horas
  - Archivos: chatbot/entrenamiento.txt (nuevo)
  - Dependencia: Chatbase configurado

- [ ] **Integrar widget chat en web**
  - Contexto: Mostrar chat en web para clientes
  - Accion: Copiar codigo widget, personalizar colores
  - Estimacion: 30 min
  - Archivos: js/chatbot-loader.js (nuevo)
  - Dependencia: Bot entrenado

- [ ] **Probar bot con preguntas reales**
  - Contexto: Verificar que responde correctamente
  - Accion: Hacer 20+ preguntas test, refinar entrenamiento
  - Estimacion: 1 hora
  - Dependencia: Widget integrado

#### Capacitacion Familia

- [ ] **Capacitar familia usar Sanity Studio**
  - Contexto: Familia debe poder editar contenido
  - Accion: Sesion 1 hora mostrando como editar producto, obra
  - Estimacion: 1 hora
  - Documentacion: Crear guia simple con capturas
  - Dependencia: Sanity funcionando

- [ ] **Crear guia rapida de uso**
  - Contexto: Familia olvida pasos, necesita documento
  - Accion: Escribir PDF/Word con pasos (con imagenes)
  - Estimacion: 2 horas
  - Archivos: docs/GUIA_FAMILIA.pdf (nuevo)

- [ ] **Dar acceso Sanity Studio a familia**
  - Contexto: Familia necesita login propio
  - Accion: Crear usuarios, enviar invitaciones
  - Estimacion: 15 min
  - Dependencia: Capacitacion completada

### 🎯 P2: Deseado (Mejoras UX)

#### Calculadora de Bloques

- [ ] **Diseñar calculadora**
  - Contexto: Cliente ingresa medidas pared → sabe cuantos bloques
  - Accion: HTML form + estilos
  - Estimacion: 2 horas
  - Archivos: calculadora.html (nuevo), css/calculadora.css (nuevo)

- [ ] **Logica de calculo**
  - Contexto: Formula: (largo/40cm) * (alto/20cm) + 5% desperdicio
  - Accion: JavaScript o Netlify Function
  - Estimacion: 2 horas
  - Archivos: js/calculadora.js o functions/calcular-bloques.js
  - Dependencia: Diseño completado

- [ ] **Integrar con formulario cotizacion**
  - Contexto: Resultado → Pre-llena formulario contacto
  - Accion: Pasar datos calculadora a form
  - Estimacion: 1 hora
  - Dependencia: Calculadora funcional

#### Mejoras SEO

- [ ] **Agregar favicon**
  - Contexto: Icono en pestana navegador
  - Accion: Ya existe images/favicon.svg, agregar a HTML
  - Estimacion: 5 min
  - Archivos: index.html

- [ ] **Optimizar metatags**
  - Contexto: Mejorar SEO Google
  - Accion: Meta description, keywords, Open Graph completos
  - Estimacion: 30 min
  - Archivos: index.html (actualizar head)

- [ ] **Comprimir imagenes**
  - Contexto: Fotos obras pueden ser pesadas
  - Accion: Pasar por TinyPNG, re-subir optimizadas
  - Estimacion: 30 min
  - Herramienta: [TinyPNG](https://tinypng.com/)

- [ ] **Agregar sitemap.xml**
  - Contexto: Google indexa mejor
  - Accion: Crear sitemap manualmente o con generador
  - Estimacion: 15 min
  - Archivos: sitemap.xml (nuevo)

- [ ] **Agregar Google Analytics**
  - Contexto: Ver cuantas visitas, de donde vienen
  - Accion: Crear cuenta GA4, agregar script
  - Estimacion: 30 min
  - Archivos: index.html (agregar GA script)

**Tiempo total Fase 2:** ~20-25 horas

---

## 📊 FASE 3: SISTEMA DE COTIZACIONES (Futuro)

**Objetivo:** Automatizar cotizaciones, guardar en base de datos
**Plazo estimado:** 1-2 meses despues Fase 2
**Estado:** 💡 Conceptual

### ⚡ P1: Importante

#### Base de Datos (Supabase)

- [ ] **Configurar proyecto Supabase**
  - Contexto: Necesitamos guardar cotizaciones, consultas
  - Accion: Crear proyecto, configurar DB
  - Estimacion: 1 hora
  - Herramienta: [Supabase](https://supabase.com/)

- [ ] **Crear tablas**
  - Contexto: Estructura datos cotizaciones, consultas
  - Accion: SQL para crear tablas (ver 01_ARQUITECTURA.md)
  - Estimacion: 1 hora
  - Archivos: SQL scripts

- [ ] **Configurar Row Level Security**
  - Contexto: Solo familia puede ver/editar datos
  - Accion: Politicas RLS en Supabase
  - Estimacion: 1 hora
  - Documentacion: [Supabase RLS](https://supabase.com/docs/guides/auth/row-level-security)

#### Netlify Functions

- [ ] **Function: Guardar cotizacion**
  - Contexto: Formulario web → Guarda en Supabase
  - Accion: Crear function serverless
  - Estimacion: 2 horas
  - Archivos: functions/cotizacion.js (nuevo)

- [ ] **Function: Notificar WhatsApp**
  - Contexto: Nueva cotizacion → Notifica a familia
  - Accion: Integrar API WhatsApp (Twilio o similar)
  - Estimacion: 3 horas
  - Archivos: functions/notificar-whatsapp.js (nuevo)
  - Nota: Puede requerir servicio pago ($1-5/mes)

- [ ] **Integrar functions con formulario**
  - Contexto: Form llama function en vez de link directo WhatsApp
  - Accion: Actualizar JS formulario
  - Estimacion: 1 hora
  - Archivos: js/main.js (actualizar)

#### Dashboard Familia

- [ ] **Capacitar usar Supabase Dashboard**
  - Contexto: Familia debe ver cotizaciones guardadas
  - Accion: Mostrar como acceder, buscar, filtrar
  - Estimacion: 30 min
  - Dependencia: Datos guardandose correctamente

- [ ] **Crear vistas personalizadas**
  - Contexto: Simplificar dashboard para familia
  - Accion: SQL views en Supabase
  - Estimacion: 1 hora
  - Ejemplo: "Ultimas 10 cotizaciones", "Cotizaciones pendientes"

### 🎯 P2: Deseado

- [ ] **Sistema de estados cotizacion**
  - Contexto: Marcar como: pendiente, respondida, completada
  - Accion: Agregar columna estado, UI para cambiar
  - Estimacion: 2 horas

- [ ] **Exportar cotizaciones Excel**
  - Contexto: Familia quiere backup o analisis
  - Accion: Boton "Exportar CSV" en Supabase o custom
  - Estimacion: 1 hora

- [ ] **Estadisticas basicas**
  - Contexto: Ver cuantas cotizaciones/mes, producto mas pedido
  - Accion: Queries SQL + visualizacion simple
  - Estimacion: 3 horas

**Tiempo total Fase 3:** ~15-20 horas

---

## 🎨 FASE 4: MEJORAS AVANZADAS (Largo plazo)

**Objetivo:** Features premium, escalar negocio
**Plazo:** 3-6 meses despues Fase 3
**Estado:** 💭 Ideas

### Blog de Construccion

- [ ] **Definir schema articulo en Sanity**
  - Contexto: Publicar consejos: "Cuantos bloques para un cuarto"
  - Estimacion: 1 hora

- [ ] **Crear seccion blog en web**
  - Contexto: blog.norteblock.com o /blog
  - Estimacion: 4 horas

- [ ] **Escribir 5 articulos iniciales**
  - Contexto: SEO + posicionamiento como expertos
  - Estimacion: 10 horas (con ayuda IA)

- [ ] **Optimizar SEO articulos**
  - Contexto: Google indexe blog
  - Estimacion: 2 horas

### Sistema de Pedidos

- [ ] **Carrito de compra simple**
  - Contexto: Cliente agrega productos, calcula total
  - Estimacion: 8 horas

- [ ] **Integracion pagos (Yape/Plin)**
  - Contexto: Cliente paga online
  - Estimacion: 6 horas
  - Nota: Requiere investigar opciones Peru

- [ ] **Panel gestion pedidos**
  - Contexto: Familia ve pedidos, marca como "enviado"
  - Estimacion: 6 horas

### Galeria Ampliable

- [ ] **Filtros galeria obras**
  - Contexto: Filtrar por tipo (casa, edificio, muro)
  - Estimacion: 3 horas

- [ ] **Lightbox imagenes**
  - Contexto: Click imagen → Ver grande con detalles
  - Estimacion: 2 horas

- [ ] **Testimonios clientes**
  - Contexto: Reseñas de clientes satisfechos
  - Estimacion: 3 horas

### Chatbot WhatsApp

- [ ] **Investigar opciones**
  - Contexto: Bot en WhatsApp (ademas del de web)
  - Opciones: Evolution API, Baileys, Twilio
  - Estimacion: 4 horas investigacion

- [ ] **Implementar bot WhatsApp**
  - Contexto: Misma IA que web, en WhatsApp
  - Estimacion: 10-15 horas
  - Nota: Puede requerir servidor ($5/mes)

### Dominio Propio

- [ ] **Comprar dominio norteblock.com**
  - Contexto: Mas profesional que .netlify.app
  - Costo: ~$12/año
  - Estimacion: 30 min configurar DNS

- [ ] **Configurar email profesional**
  - Contexto: contacto@norteblock.com real
  - Opciones: Google Workspace ($6/mes) o Zoho gratis
  - Estimacion: 1 hora

### App Mobile (Muy futuro)

- [ ] **Evaluar necesidad app**
  - Contexto: ¿Vale la pena vs web responsive?
  - Estimacion: Solo si negocio crece mucho

**Tiempo total Fase 4:** 50-80 horas (distribuido en meses)

---

## ❌ BLOQUEADOS / DESCARTADOS

### Bloqueados

- [❌] **Integracion sistema facturacion** (Bloqueado)
  - Razon: Requiere RUC, sistema contable formal
  - Solucion alternativa: Cuando negocio formalice

- [❌] **Marketplace multi-vendedor** (Bloqueado)
  - Razon: Solo un negocio (Norteblock), innecesario
  - No aplica

### Descartados

- [❌] **Version en ingles** (Descartado)
  - Razon: Mercado es 100% local (Monsefu)
  - No tiene sentido

- [❌] **Integracion redes sociales** (Descartado por ahora)
  - Razon: Familia no usa Facebook/Instagram activamente
  - Revisar si crean redes en futuro

---

## 📚 BACKLOG (Ideas sin priorizar)

Ideas que surgieron pero no tienen fecha:

- Programa de referidos (cliente refiere → descuento)
- Calculadora avanzada (incluye cemento, arena necesaria)
- Comparador de presupuestos (bloques vs ladrillo)
- Mapa interactivo de entregas realizadas
- Sistema de inventario en tiempo real
- Integracion con Google Maps (ver ubicacion fabrica)
- Chatbot por voz (asistente de voz)
- AR (realidad aumentada): Ver bloque en 3D

---

## 📊 METRICAS Y PRIORIDADES

### Resumen por fase

| Fase | Estado | Tareas | Tiempo estimado | Prioridad |
|------|--------|--------|-----------------|-----------|
| Fase 1 | ✅ Completada | 12 | 10 horas | - |
| Fase 2 | 📋 Planificada | 15 | 20-25 horas | ALTA |
| Fase 3 | 💡 Conceptual | 10 | 15-20 horas | MEDIA |
| Fase 4 | 💭 Ideas | 15+ | 50-80 horas | BAJA |

### Enfoque recomendado

**Siguiente sprint (2-4 semanas):**

**Semana 1-2: Dashboard CMS**
1. ✅ Configurar Sanity (P0)
2. ✅ Migrar contenido (P0)
3. ✅ Conectar web (P0)
4. ✅ Capacitar familia (P1)

**Semana 3: Chat IA**
1. ✅ Configurar Chatbase (P1)
2. ✅ Entrenar bot (P1)
3. ✅ Integrar widget (P1)
4. ✅ Probar con familia (P1)

**Semana 4: Pulir**
1. ✅ Calculadora bloques (P2)
2. ✅ Mejoras SEO (P2)
3. ✅ Pruebas con clientes reales

**Criterio de exito Fase 2:**
- [x] Familia puede editar productos sin ayuda
- [x] Bot IA responde 80%+ preguntas correctamente
- [x] Familia recibe al menos 5 consultas via web/mes
- [x] Calculadora funciona correctamente

---

## 🎯 PROXIMOS PASOS INMEDIATOS

**Esta semana:**
1. Decidir: ¿Empezar Fase 2 ya o esperar?
2. Si si, crear cuenta Sanity
3. Leer documentacion Sanity (1 hora)
4. Planificar sesion con familia (explicar dashboard)

**Siguiente sesion con IA:**
1. Leer docs/00_CONTEXTO_PROYECTO.md
2. Leer docs/03_PENDIENTES.md (este archivo)
3. Decidir tarea especifica de Fase 2
4. Implementar paso a paso

---

**Ultima actualizacion:** 2025-01-28
**Actualizado por:** Claude (Anthropic)
**Proxima revision:** Al completar Fase 2
