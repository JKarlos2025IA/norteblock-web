# DECISIONES TECNICAS - Norteblock Web

**Proyecto:** Norteblock - Sitio Web Familiar
**Proposito:** Registro de decisiones arquitectonicas importantes (ADR)
**Formato:** Architecture Decision Records

---

## Indice de Decisiones

1. [Vanilla JS sin frameworks](#decision-1-vanilla-js-sin-frameworks)
2. [Netlify como hosting](#decision-2-netlify-como-hosting)
3. [Sanity como CMS](#decision-3-sanity-como-cms-para-dashboard)
4. [Chatbase para IA](#decision-4-chatbase-para-chat-ia)
5. [Supabase como base de datos](#decision-5-supabase-como-base-de-datos)
6. [JAMstack como arquitectura](#decision-6-jamstack-como-arquitectura)
7. [Mobile-first design](#decision-7-mobile-first-design)
8. [WhatsApp como canal principal](#decision-8-whatsapp-como-canal-principal)

---

## Decision 1: Vanilla JS sin frameworks

**Fecha:** 2025-11 (inicio proyecto)
**Estado:** ✅ Activa
**Contexto:** Definir tecnologias para construir el sitio web

### Problema

Necesitamos crear un sitio web interactivo. Opciones:
- Vanilla JavaScript
- React
- Vue
- Next.js
- Astro

### Opciones consideradas

#### Opcion A: React

**Pros:**
- Popular, mucha documentacion
- Componentes reutilizables
- Ecosistema grande
- Facil encontrar ayuda

**Contras:**
- Requiere npm, node_modules (pesado)
- Build process complejo
- Curva de aprendizaje alta
- Overkill para sitio simple
- Juan NO sabe React
- Familia NO podra mantenerlo

#### Opcion B: Next.js

**Pros:**
- SSR out of the box
- SEO optimizado
- Routing automatico

**Contras:**
- Aun mas complejo que React
- Requiere servidor o Vercel
- Juan NO lo conoce
- Innecesario para landing page

#### Opcion C: Vanilla JavaScript

**Pros:**
- Cero dependencias
- Rapido de cargar (<1 segundo)
- Simple de mantener
- No requiere build
- Total control
- Juan puede entenderlo con ayuda
- Familia puede hacer cambios minimos

**Contras:**
- Mas codigo manual
- Sin componentes reutilizables nativos
- Manipulacion DOM manual

### Decision tomada

**Vanilla JavaScript (Opcion C)**

### Razonamiento

1. **Simplicidad:** Sitio es landing page simple, no necesita framework
2. **Velocidad:** Sin dependencias = carga instantanea
3. **Mantenibilidad:** Juan NO es programador, vanilla es mas entendible
4. **Portabilidad:** Funciona en cualquier navegador sin compilar
5. **Costo cero:** No requiere infrastructure compleja
6. **Futuro CMS:** Contenido dinamico vendra de Sanity, no de componentes React

### Consecuencias

**Positivas:**
- Proyecto pesa <100 KB vs 2+ MB con framework
- Netlify deploy es instantaneo
- Facil de debuggear (no source maps)
- Sin vulnerabilidades de dependencias
- Juan puede hacer ajustes con ayuda de IA

**Negativas:**
- Mas codigo repetitivo (funciones helper)
- Manipulacion DOM manual
- Sin hot reload (refresh manual)
- Si crece mucho, podria necesitar refactor

**Riesgos:**
- Si proyecto necesita SPA complejo (routing, estado global), sera dificil
- Mitigacion: Usar Sanity para dinamismo, mantener JS simple

### Cuando revisar esta decision

Si el proyecto:
- Necesita routing complejo (multiples paginas con estado)
- Requiere estado global compartido
- Se vuelve muy dificil de mantener (>2000 lineas JS)
- Familia necesita editar logica (no solo contenido)

**Nota:** Con Sanity CMS, es poco probable que necesitemos framework.

---

## Decision 2: Netlify como hosting

**Fecha:** 2025-11-19
**Estado:** ✅ Activa
**Contexto:** Donde publicar el sitio web

### Problema

Necesitamos hosting para el sitio. Opciones:
- Hosting tradicional (cPanel)
- Netlify
- Vercel
- GitHub Pages
- Servidor propio

### Opciones consideradas

#### Opcion A: Hosting tradicional (cPanel)

**Pros:**
- Familiar para algunos
- Control total

**Contras:**
- Costo mensual (~$5-10/mes)
- Configuracion manual (FTP, SSL)
- Sin CI/CD automatico
- Lento de actualizar

#### Opcion B: Vercel

**Pros:**
- Excelente para Next.js
- Deploy automatico
- CDN global

**Contras:**
- Optimizado para frameworks
- Funciones serverless limitadas en free tier
- Menos conocido que Netlify

#### Opcion C: GitHub Pages

**Pros:**
- Gratis
- Deploy desde GitHub

**Contras:**
- Solo sitios estaticos (limitado)
- Sin serverless functions
- SSL solo para dominio GitHub

#### Opcion D: Netlify

**Pros:**
- Gratis para proyectos personales
- Deploy automatico desde GitHub
- CDN global incluido
- SSL gratuito
- Serverless functions incluidas
- Forms sin backend
- Muy facil de usar

**Contras:**
- Limites en free tier (100GB bandwidth/mes)
- Vendor lock-in parcial

### Decision tomada

**Netlify (Opcion D)**

### Razonamiento

1. **Costo:** Gratis hasta escalar mucho (improbable para inicio)
2. **Simplicidad:** Push a GitHub → Deploy automatico
3. **Funcionalidades:** Forms, functions, CDN incluido
4. **Escalabilidad:** Si negocio crece, facil upgrade
5. **Juan ya lo usa:** Experiencia previa en otros proyectos
6. **Familia no toca:** Deploy es automatico, familia no necesita saber

### Consecuencias

**Positivas:**
- Deploy en segundos
- HTTPS automatico
- CDN mundial (sitio rapido en Peru)
- Preview deploys (probar antes de publicar)
- Rollback facil si algo falla
- Forms sin backend (si necesitamos)

**Negativas:**
- Dependencia de Netlify (cambiar seria trabajoso)
- Limite 100GB/mes (suficiente, pero hay limite)
- Functions tienen limite 125k invocaciones/mes

**Riesgos:**
- Si trafico explota, podria exceder free tier
- Mitigacion: Monitorear uso, upgrade si es necesario ($19/mes)

### Cuando revisar esta decision

Si:
- Trafico excede limites free tier consistentemente
- Necesitamos features que Netlify no tiene
- Costo de upgrade no se justifica vs alternativas
- Problemas de performance o disponibilidad

**Nota:** Por ahora, Netlify es perfecto y gratis.

---

## Decision 3: Sanity como CMS para dashboard

**Fecha:** 2025-01-28 (planificacion Fase 2)
**Estado:** 🔄 Planificada (no implementada aun)
**Contexto:** Familia necesita editar contenido sin tocar codigo

### Problema

Familia NO sabe codigo pero necesita:
- Cambiar precios de productos
- Agregar/quitar fotos de obras
- Actualizar textos (horarios, ubicacion, etc)
- Agregar nuevos productos

Opciones:
- Editar HTML manualmente (imposible para familia)
- Usar CMS headless
- Usar CMS tradicional (WordPress)
- Construir dashboard custom

### Opciones consideradas

#### Opcion A: WordPress

**Pros:**
- Conocido
- Muchos plugins
- Temas gratis

**Contras:**
- Pesado (PHP, MySQL, hosting complejo)
- Requiere hosting diferente
- Lento
- Vulnerable a ataques
- Dificultar migrar de estatico a WordPress

#### Opcion B: Strapi (Headless CMS)

**Pros:**
- Open source
- Control total
- Flexible
- Gratis self-hosted

**Contras:**
- Requiere servidor Node.js
- Configuracion tecnica
- Familia necesita servidor ($5/mes minimo)
- Mas complejo de configurar que Sanity

#### Opcion C: Sanity.io (Headless CMS)

**Pros:**
- Cloud-hosted (sin servidor)
- Interfaz super intuitiva
- Drag & drop para imagenes
- API automatica
- Free tier generoso (100k requests/mes)
- Tiempo real (cambios instantaneos)
- Schemas customizables

**Contras:**
- Vendor lock-in
- Limite en free tier (suficiente pero existe)
- Requiere aprender Sanity schemas (Juan, no familia)

#### Opcion D: Dashboard custom

**Pros:**
- Control total
- Sin costos externos

**Contras:**
- Juan tendria que programarlo (semanas de trabajo)
- Mantenimiento largo plazo
- Requiere backend + base de datos
- Costoso en tiempo

### Decision tomada

**Sanity.io (Opcion C)**

### Razonamiento

1. **Facilidad familia:** Interfaz visual, no requiere conocimiento tecnico
2. **Costo:** Gratis hasta 100k requests (mas que suficiente)
3. **Sin servidor:** Familia no paga ni mantiene servidor
4. **Rapidez desarrollo:** Juan configura schemas en 2-3 horas, no semanas
5. **Escalable:** Si crece, facil upgrade
6. **API lista:** Consumir datos es simple (fetch desde JS)

### Consecuencias

**Positivas:**
- Familia edita contenido desde panel visual
- Cambios aparecen en web instantaneamente
- Juan no recibe llamadas "cambia este texto"
- Imagenes optimizadas automaticamente
- Versionado (revertir cambios si se equivocan)
- WYSIWYG (What You See Is What You Get)

**Negativas:**
- Dependencia de Sanity (cambiar seria trabajoso)
- Limite free tier (100k requests = ~1000 visitas/dia con 100 requests/visita)
- Curva aprendizaje minima para familia (1 hora de capacitacion)

**Riesgos:**
- Si Sanity cierra o cambia precios drasticamente
- Mitigacion: Exportar datos es facil, migrar a Strapi seria posible

### Cuando revisar esta decision

Si:
- Trafico excede 100k requests/mes consistentemente
- Sanity cambia precios a inasequibles
- Necesitamos features que Sanity no tiene
- Queremos control total on-premise

### Plan de implementacion

**Fase 1: Setup (1-2 horas)**
- Crear proyecto Sanity
- Definir schemas (producto, obra, configuracion)
- Configurar Sanity Studio

**Fase 2: Integracion (2-3 horas)**
- Conectar web a Sanity API
- Migrar contenido actual a Sanity
- Probar cambios reflejan en web

**Fase 3: Capacitacion (1 hora)**
- Enseñar a familia usar panel
- Documentar procesos comunes
- Dar acceso con email/password

---

## Decision 4: Chatbase para Chat IA

**Fecha:** 2025-01-28 (planificacion Fase 2)
**Estado:** 🔄 Planificada
**Contexto:** Responder preguntas frecuentes automaticamente con IA

### Problema

Familia recibe muchas consultas repetitivas:
- "¿Cuanto cuesta el bloque?"
- "¿Tienen delivery?"
- "¿Donde estan ubicados?"
- "¿Cuantos bloques necesito para mi pared?"

Opciones:
- Responder manualmente siempre (agotador)
- Chatbot pre-programado (limitado)
- IA conversacional (flexible)

### Opciones consideradas

#### Opcion A: Chatbot pre-programado (Typebot)

**Pros:**
- Gratuito
- Control total de flujo
- Facil de configurar

**Contras:**
- No es inteligente (solo sigue arbol de decision)
- Requiere anticipar todas las preguntas
- Rigido, no natural

#### Opcion B: Voiceflow

**Pros:**
- Visual, drag & drop
- Integra IA (GPT)
- Multicanal (web, WhatsApp, etc)

**Contras:**
- Free tier muy limitado (10 conversaciones/mes)
- Plan pago $30/mes (caro para inicio)
- Complejidad innecesaria

#### Opcion C: Chatbase

**Pros:**
- Entrenamiento simple (sube documentos o texto)
- Free tier generoso (30 mensajes/mes)
- Widget facil integrar en web
- Aprende de conversaciones
- Respuestas naturales (GPT-4)
- No requiere programacion

**Contras:**
- Limite mensajes (30/mes free, $19/mes para 2000)
- Menor control que Voiceflow
- Requiere entrenar bien para evitar respuestas incorrectas

#### Opcion D: Custom con OpenAI API

**Pros:**
- Control total
- Sin limites propios

**Contras:**
- Juan debe programar todo
- Costo por token (inestable)
- Mantenimiento constante
- Semanas de desarrollo

### Decision tomada

**Chatbase (Opcion C)**

### Razonamiento

1. **Facilidad:** Entrenar bot es copiar/pegar info de Norteblock
2. **Costo:** 30 mensajes/mes gratis (suficiente para validar)
3. **Calidad:** Usa GPT-4, respuestas naturales
4. **Rapidez:** Configurar en 1 hora vs semanas custom
5. **Sin programacion:** Familia podria entrenar bot (agregar info nueva)
6. **Escalable:** $19/mes para 2000 mensajes es razonable si funciona

### Consecuencias

**Positivas:**
- IA responde 24/7, familia descansa
- Respuestas instantaneas (clientes no esperan)
- Filtra consultas simples, deriva complejas a WhatsApp
- Aprende de conversaciones (mejora con tiempo)
- Reduce carga de trabajo familia significativamente

**Negativas:**
- Limite 30 mensajes/mes en free tier (si tiene exito, necesitara pagar)
- Puede dar respuestas incorrectas si mal entrenado
- Dependencia de Chatbase

**Riesgos:**
- IA da informacion incorrecta (precios equivocados, promesas falsas)
- Mitigacion: Entrenar bien, probar extensivamente, siempre deriva a humano para cotizaciones

### Cuando revisar esta decision

Si:
- Excede 30 mensajes/mes y $19/mes no se justifica
- Calidad respuestas es mala consistentemente
- Necesitamos integracion WhatsApp directa (no solo web)
- Queremos mas control (entonces custom con OpenAI)

### Plan de implementacion

**Fase 1: Entrenamiento (1 hora)**
- Crear cuenta Chatbase
- Subir info: productos, precios, ubicacion, FAQs
- Probar conversaciones

**Fase 2: Integracion (30 min)**
- Copiar codigo widget
- Agregar a web
- Personalizar colores (naranja Norteblock)

**Fase 3: Validacion (1 semana)**
- Probar con familia
- Refinar entrenamiento segun errores
- Monitorear conversaciones

---

## Decision 5: Supabase como base de datos

**Fecha:** 2025-01-28 (planificacion Fase 2)
**Estado:** 🔄 Planificada
**Contexto:** Guardar cotizaciones, consultas, pedidos

### Problema

Necesitamos almacenar:
- Cotizaciones que llegan via web
- Consultas del chatbot IA
- Pedidos futuros
- Inventario (futuro)

Opciones:
- No guardar nada (actual - todo por WhatsApp)
- Google Sheets (hacky)
- Base de datos real

### Opciones consideradas

#### Opcion A: Google Sheets + Zapier

**Pros:**
- Familia conoce Sheets
- Facil ver datos
- Gratis

**Contras:**
- No es base de datos real
- Limites de API
- Lento
- No escalable
- Hacky

#### Opcion B: Firebase (Google)

**Pros:**
- NoSQL facil
- Gratis generoso
- Auth incluido

**Contras:**
- NoSQL (sin relaciones, puede ser confuso)
- Vendor lock-in Google
- Queries limitadas

#### Opcion C: MongoDB Atlas

**Pros:**
- NoSQL
- Free tier

**Contras:**
- Curva aprendizaje NoSQL
- No tan generoso free tier
- Menos features que Supabase

#### Opcion D: Supabase

**Pros:**
- PostgreSQL (SQL real, potente)
- Gratis hasta 500MB + 2GB bandwidth
- Dashboard visual para familia
- Auth incluido
- Realtime subscriptions
- API REST automatica
- Storage para imagenes (si necesitamos)

**Contras:**
- Vendor lock-in
- Limite free tier (suficiente pero existe)
- PostgreSQL puede ser complejo (pero Supabase lo simplifica)

### Decision tomada

**Supabase (Opcion D)**

### Razonamiento

1. **SQL real:** Relaciones, queries complejos si escalamos
2. **Dashboard:** Familia puede ver cotizaciones sin programacion
3. **Gratis:** 500MB + 2GB bandwidth suficiente para años
4. **API automatica:** Juan no programa backend, Supabase genera APIs
5. **Auth:** Si necesitamos login familia, ya incluido
6. **Realtime:** Notificaciones cuando llega cotizacion

### Consecuencias

**Positivas:**
- Cotizaciones guardadas, no se pierden
- Familia puede buscar cotizaciones antiguas
- Metricas: cuantas consultas/mes, productos mas pedidos
- Base para sistema pedidos futuro
- Backups automaticos

**Negativas:**
- Dependencia Supabase
- Limite 500MB (suficiente pero existe)
- Curva aprendizaje SQL para Juan (minima)

**Riesgos:**
- Si excede limites free tier
- Mitigacion: Monitorear uso, $25/mes tier siguiente

### Cuando revisar esta decision

Si:
- Excede 500MB o 2GB bandwidth consistentemente
- Necesitamos features que Supabase no tiene
- Queremos database on-premise

### Plan de implementacion

**Fase 1: Setup (1 hora)**
- Crear proyecto Supabase
- Crear tablas (cotizaciones, consultas)
- Configurar Row Level Security

**Fase 2: Integracion (2 horas)**
- Netlify Functions llaman Supabase API
- Guardar cotizaciones desde formulario
- Guardar consultas chatbot

**Fase 3: Dashboard (1 hora)**
- Capacitar familia usar dashboard Supabase
- Crear vistas simples (ultimas cotizaciones)

---

## Decision 6: JAMstack como arquitectura

**Fecha:** 2025-01-28 (planificacion Fase 2)
**Estado:** 🔄 Planificada
**Contexto:** Arquitectura general del sistema v2.0

### Problema

¿Como organizar frontend, backend, CMS, IA?

Opciones:
- Monolito tradicional (todo en un servidor)
- Microservicios completo
- JAMstack (estatico + APIs)

### Opciones consideradas

#### Opcion A: Monolito (PHP/WordPress)

**Pros:**
- Todo en un lugar
- Familiar para muchos

**Contras:**
- Pesado, lento
- Dificil escalar
- Requiere servidor completo
- Vulnerable
- Caro

#### Opcion B: Microservicios completo

**Pros:**
- Escalable
- Cada servicio independiente

**Contras:**
- Complejidad extrema
- Overkill para este proyecto
- Caro

#### Opcion C: JAMstack

**Pros:**
- Frontend estatico (rapido, seguro)
- APIs para dinamismo
- Escala horizontal facil
- Costo bajo (muchos servicios gratis)
- Performance excelente

**Contras:**
- Requiere multiples servicios (Sanity, Supabase, etc)
- Orquestacion necesaria

### Decision tomada

**JAMstack (Opcion C)**

### Razonamiento

1. **Performance:** Estatico en CDN = milisegundos de carga
2. **Seguridad:** Sin backend expuesto = menos ataques
3. **Costo:** Casi todo gratis (Netlify, Sanity, Supabase free tiers)
4. **Escalabilidad:** CDN escala automatico
5. **Developer Experience:** Juan trabaja con APIs simples

### Consecuencias

**Positivas:**
- Web ultra rapida
- Casi imposible hackear (sin backend tradicional)
- Costo operacional casi cero
- Facil de mantener
- Cada servicio se puede cambiar sin afectar otros

**Negativas:**
- Dependencia de multiples servicios
- Si un servicio falla, parte del sistema falla
- Mas complejo que monolito simple

**Riesgos:**
- Alguna API externa cae (Sanity, Chatbase)
- Mitigacion: Manejar errores, fallbacks, caché

### Cuando revisar esta decision

Si:
- Costos de servicios externos superan $50/mes
- Complejidad se vuelve inmanejable
- Performance no es prioridad

---

## Decision 7: Mobile-first design

**Fecha:** 2025-11 (inicio proyecto)
**Estado:** ✅ Activa
**Contexto:** Enfoque de diseño responsive

### Problema

¿Diseñar primero para desktop o mobile?

### Opciones consideradas

#### Opcion A: Desktop-first

**Pros:**
- Mas espacio, mas facil diseñar

**Contras:**
- Adaptar a mobile es mas dificil
- Mobile es mayoria de usuarios

#### Opcion B: Mobile-first

**Pros:**
- Mobile es 70%+ usuarios en Peru
- Mas facil agregar espacio (desktop) que quitarlo (mobile)
- Performance mejor (CSS mobile primero)

**Contras:**
- Menos espacio para diseñar

### Decision tomada

**Mobile-first (Opcion B)**

### Razonamiento

1. **Estadisticas:** 70%+ usuarios en Peru usan mobile
2. **Clientes target:** Maestros de obra usan celular
3. **Progressive enhancement:** Facil agregar features desktop despues
4. **Performance:** Mobile carga solo CSS necesario

### Consecuencias

**Positivas:**
- Web funciona perfecto en celular
- Performance excelente en mobile
- Touch-friendly (botones grandes)

**Negativas:**
- Desktop puede sentirse basico (pero funcional)

---

## Decision 8: WhatsApp como canal principal

**Fecha:** 2025-11 (inicio proyecto)
**Estado:** ✅ Activa
**Contexto:** Canal de comunicacion con clientes

### Problema

¿Como deben contactar clientes?

Opciones:
- Formulario con email
- Telefono
- WhatsApp
- Chat web exclusivo

### Opciones consideradas

#### Opcion A: Email

**Pros:**
- Profesional

**Contras:**
- Familia no revisa email constantemente
- Clientes prefieren WhatsApp

#### Opcion B: WhatsApp

**Pros:**
- Familia ya lo usa 24/7
- Clientes lo prefieren en Peru
- Instantaneo
- Permite fotos (obras, planos)
- Confianza (ven negocio real)

**Contras:**
- Menos formal

### Decision tomada

**WhatsApp como canal principal**

### Razonamiento

1. **Habito:** Familia y clientes ya usan WhatsApp
2. **Instantaneo:** Respuesta rapida
3. **Visual:** Pueden enviar fotos de proyectos
4. **Confianza:** Chat directo genera confianza

### Consecuencias

**Positivas:**
- Conversion alta (facil contactar)
- Familia responde rapido
- Cliente ve negocio activo (online/offline)

**Negativas:**
- Menos tracking formal
- No escalable si volumen explota

---

**Ultima actualizacion:** 2025-01-28
**Total de decisiones:** 8
