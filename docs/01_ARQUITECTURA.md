# ARQUITECTURA - Norteblock Web

**Proyecto:** Norteblock - Sitio Web Familiar
**Version:** 1.0 → 2.0 (en planificacion)
**Ultima actualizacion:** 2025-01-28

---

## 🏗️ VISION GENERAL

### Descripcion de alto nivel

**Estado Actual (v1.0):**
Landing page estatica de una sola pagina (SPA) con HTML/CSS/JS vanilla, publicada en Netlify.

**Vision Futura (v2.0):**
Sistema completo con:
- Frontend estatico (mantiene simplicidad)
- Headless CMS (dashboard para familia)
- Chat IA integrado (atencion automatica)
- Base de datos (cotizaciones, consultas)
- Funciones serverless (notificaciones, logica backend)

### Patron arquitectonico

**Actual:** Arquitectura estatica tradicional
```
HTML + CSS + JS → Netlify CDN → Cliente
```

**Futuro:** JAMstack (JavaScript, APIs, Markup)
```
Frontend estatico ← API → Sanity CMS (dashboard familia)
        ↓
    Chatbase IA (widget integrado)
        ↓
    Supabase DB (datos persistentes)
        ↓
    Netlify Functions (serverless backend)
```

---

## 📊 ARQUITECTURA ACTUAL (v1.0)

### Diagrama de componentes

```
┌─────────────────────────────────────────────────────────┐
│                   CLIENTE (Navegador)                    │
└────────────────────────┬────────────────────────────────┘
                         │
                         ▼
            ┌────────────────────────┐
            │    Netlify CDN         │
            │  (Hosting estatico)    │
            └────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
    ┌─────────┐    ┌─────────┐    ┌──────────┐
    │ HTML    │    │  CSS    │    │    JS    │
    │ (389 l) │    │ Styles  │    │  main.js │
    └─────────┘    └─────────┘    └──────────┘
         │               │               │
         └───────────────┴───────────────┘
                         │
                         ▼
                  ┌──────────────┐
                  │   Images/    │
                  │  - Logo      │
                  │  - Productos │
                  │  - Obras (8) │
                  └──────────────┘
                         │
                         ▼
              ┌──────────────────────┐
              │   Integraciones      │
              │  - WhatsApp Business │
              │  - Google Fonts      │
              │  - Font Awesome      │
              └──────────────────────┘
```

### Flujo de datos (Actual)

#### Escenario 1: Usuario visita web

```
Usuario ingresa URL
    ↓
Netlify CDN sirve archivos estaticos
    ↓
Navegador renderiza HTML
    ↓
CSS aplica estilos responsive
    ↓
JS inicializa interactividad:
    - Menu hamburguesa
    - Carrusel de obras
    - Smooth scroll
    - Validacion formulario
```

#### Escenario 2: Usuario contacta via formulario

```
Usuario llena formulario
    ↓
JS captura datos (nombre, telefono, mensaje)
    ↓
Genera URL de WhatsApp con datos pre-llenados
    ↓
Abre WhatsApp Web/App
    ↓
Usuario envia mensaje manualmente
    ↓
Familia recibe en WhatsApp Business
```

#### Escenario 3: Usuario hace click en boton WhatsApp

```
Usuario click boton flotante o CTA
    ↓
Abre link wa.me/51940267730
    ↓
WhatsApp Web/App con mensaje pre-escrito
    ↓
Usuario envia consulta
    ↓
Familia responde manualmente
```

---

## 🔮 ARQUITECTURA FUTURA (v2.0)

### Diagrama de sistema completo

```
┌──────────────────────────────────────────────────────────────────┐
│                      CLIENTE (Navegador)                         │
│  - Ve web actualizada con contenido desde CMS                   │
│  - Chatea con IA                                                 │
│  - Usa calculadora de bloques                                    │
└────────────────────────┬─────────────────────────────────────────┘
                         │
                         ▼
            ┌────────────────────────────┐
            │      Netlify CDN           │
            │   (Frontend estatico)      │
            │  - index.html              │
            │  - calculadora.html        │
            │  - blog/ (futuro)          │
            └────────┬───────────────────┘
                     │
       ┌─────────────┼──────────────┬──────────────┐
       ▼             ▼              ▼              ▼
┌──────────┐  ┌──────────┐  ┌───────────┐  ┌──────────────┐
│ Sanity   │  │ Chatbase │  │ Supabase  │  │   Netlify    │
│   CMS    │  │  Chat IA │  │    DB     │  │  Functions   │
│          │  │          │  │           │  │              │
│ Dashboard│  │  Widget  │  │PostgreSQL │  │ Serverless   │
│  Visual  │  │ Entrenado│  │           │  │   Backend    │
└──────────┘  └──────────┘  └───────────┘  └──────────────┘
     │              │              │              │
     │              │              │              │
     ▼              ▼              ▼              ▼
┌────────────────────────────────────────────────────────┐
│            FAMILIA (Panel Administrativo)              │
│  - Edita productos (Sanity Studio)                    │
│  - Ve consultas (Supabase Dashboard)                  │
│  - Revisa metricas (Analytics)                        │
└────────────────────────────────────────────────────────┘
```

### Componentes principales

#### 1. Frontend Estatico (Netlify)

**Responsabilidad:** Interfaz de usuario

**Archivos:**
```
public/
├── index.html                    # Landing principal
├── calculadora.html              # Calculadora de bloques
├── blog/                         # Blog futuro
│   ├── index.html
│   └── posts/
├── css/
│   ├── styles.css               # Estilos base
│   └── calculadora.css          # Estilos calculadora
├── js/
│   ├── main.js                  # Funciones principales
│   ├── sanity-client.js         # Consume API Sanity
│   ├── calculadora.js           # Logica calculadora
│   └── chatbot-loader.js        # Carga widget Chatbase
└── images/
    └── [estaticos]
```

**Tecnologias:**
- HTML5 (semantico)
- CSS3 (variables, grid, flexbox)
- JavaScript ES6+ (fetch API, async/await)

#### 2. Sanity CMS (Dashboard)

**Responsabilidad:** Gestion de contenido por familia

**Esquemas de datos:**

```javascript
// schemas/producto.js
{
  name: 'producto',
  title: 'Producto',
  type: 'document',
  fields: [
    {
      name: 'nombre',
      title: 'Nombre del Producto',
      type: 'string',
      validation: Rule => Rule.required()
    },
    {
      name: 'descripcion',
      title: 'Descripcion',
      type: 'text',
      rows: 4
    },
    {
      name: 'medidas',
      title: 'Medidas',
      type: 'string',
      placeholder: 'Ej: 15x20x40 cm'
    },
    {
      name: 'caracteristicas',
      title: 'Caracteristicas',
      type: 'array',
      of: [{type: 'string'}]
    },
    {
      name: 'imagen',
      title: 'Imagen',
      type: 'image',
      options: {hotspot: true}
    },
    {
      name: 'precio',
      title: 'Precio (opcional)',
      type: 'number'
    },
    {
      name: 'activo',
      title: 'Mostrar en web',
      type: 'boolean',
      initialValue: true
    }
  ]
}
```

```javascript
// schemas/obra.js
{
  name: 'obra',
  title: 'Proyecto/Obra',
  type: 'document',
  fields: [
    {
      name: 'titulo',
      title: 'Titulo',
      type: 'string'
    },
    {
      name: 'descripcion',
      title: 'Descripcion',
      type: 'text'
    },
    {
      name: 'imagenes',
      title: 'Fotos',
      type: 'array',
      of: [{type: 'image'}]
    },
    {
      name: 'fecha',
      title: 'Fecha',
      type: 'date'
    },
    {
      name: 'ubicacion',
      title: 'Ubicacion',
      type: 'string'
    }
  ]
}
```

```javascript
// schemas/configuracion.js
{
  name: 'configuracion',
  title: 'Configuracion General',
  type: 'document',
  fields: [
    {
      name: 'whatsapp',
      title: 'Numero WhatsApp',
      type: 'string',
      validation: Rule => Rule.required()
    },
    {
      name: 'email',
      title: 'Email de Contacto',
      type: 'string'
    },
    {
      name: 'ubicacion',
      title: 'Direccion',
      type: 'text'
    },
    {
      name: 'horarios',
      title: 'Horarios de Atencion',
      type: 'string'
    },
    {
      name: 'mensaje_bienvenida',
      title: 'Mensaje Hero',
      type: 'text'
    }
  ]
}
```

**Panel de administracion:**
- URL: norteblock.sanity.studio (ejemplo)
- Acceso: Email + Password (familia)
- Interfaz: Visual drag & drop, WYSIWYG

#### 3. Chatbase (Chat IA)

**Responsabilidad:** Responder preguntas automaticamente

**Entrenamiento:**

Archivo: `chatbot/entrenamiento.txt`
```
# INFORMACION NORTEBLOCK

## Productos
Vendemos bloques de concreto de alta calidad.
Medida principal: 15x20x40 cm
Material: Concreto con cemento certificado
Uso: Construccion de muros, casas, edificios

## Precios
[Familia actualiza esto en Sanity, bot lo consume]

## Entrega
Entregamos a domicilio en Monsefu y alrededores.
Radio de cobertura: 20 km desde Monsefu
Tiempo de entrega: 24-48 horas

## Contacto
WhatsApp: +51 940 267 730
Ubicacion: Monsefu, Lambayeque (11 km de Chiclayo)

## Preguntas frecuentes
P: ¿Cuantos bloques necesito?
R: Usa nuestra calculadora en la web, o dime las medidas de tu proyecto.

P: ¿Tienen delivery?
R: Si, entregamos a domicilio en Monsefu y zonas cercanas.

P: ¿Cual es el precio?
R: [Deriva a WhatsApp para cotizacion personalizada]
```

**Widget configuracion:**
```javascript
// js/chatbot-loader.js
window.embeddedChatbotConfig = {
  chatbotId: "XXXXX", // ID de Chatbase
  domain: "www.chatbase.co",
  position: "bottom-right",
  primaryColor: "#E67E22", // Naranja Norteblock
  greeting: "Hola! ¿En que puedo ayudarte?",
  placeholder: "Escribe tu pregunta..."
}
```

**Flujo de conversacion:**

```
Usuario: "Cuanto cuesta el bloque?"
    ↓
IA: "El precio varia segun cantidad y ubicacion.
     Para una cotizacion exacta, ¿me compartes cuantos
     bloques necesitas y tu ubicacion?"
    ↓
Usuario: "Necesito 500 bloques en Chiclayo"
    ↓
IA: "Perfecto! Te conecto con nuestro equipo por WhatsApp
     para enviarte la cotizacion. [Boton WhatsApp]"
    ↓
Abre WhatsApp con contexto: "Cliente necesita 500 bloques,
entrega en Chiclayo"
```

#### 4. Supabase (Base de Datos)

**Responsabilidad:** Almacenar cotizaciones, consultas, pedidos

**Tablas:**

```sql
-- Tabla: cotizaciones
CREATE TABLE cotizaciones (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  created_at TIMESTAMP DEFAULT NOW(),
  nombre VARCHAR(255),
  telefono VARCHAR(20),
  cantidad_bloques INTEGER,
  ubicacion_entrega TEXT,
  mensaje TEXT,
  estado VARCHAR(50) DEFAULT 'pendiente', -- pendiente, respondida, completada
  origen VARCHAR(50) -- 'formulario_web', 'chat_ia', 'whatsapp'
);

-- Tabla: productos_inventario (futuro)
CREATE TABLE productos_inventario (
  id UUID PRIMARY KEY,
  nombre VARCHAR(255),
  stock INTEGER,
  actualizado_at TIMESTAMP
);

-- Tabla: consultas_chatbot (para mejorar IA)
CREATE TABLE consultas_chatbot (
  id UUID PRIMARY KEY,
  created_at TIMESTAMP DEFAULT NOW(),
  pregunta TEXT,
  respuesta TEXT,
  fue_util BOOLEAN
);
```

**Acceso:**
- URL: app.supabase.com/project/norteblock
- Dashboard visual para ver datos
- API REST automatica

#### 5. Netlify Functions (Serverless)

**Responsabilidad:** Logica backend sin servidor

**Funciones:**

```javascript
// functions/cotizacion.js
// Recibe datos formulario → Guarda en Supabase → Notifica WhatsApp

exports.handler = async (event) => {
  const {nombre, telefono, cantidad, ubicacion, mensaje} = JSON.parse(event.body);

  // 1. Guardar en Supabase
  const {data, error} = await supabase
    .from('cotizaciones')
    .insert([{
      nombre,
      telefono,
      cantidad_bloques: cantidad,
      ubicacion_entrega: ubicacion,
      mensaje,
      origen: 'formulario_web'
    }]);

  // 2. Enviar notificacion WhatsApp a familia (via API de terceros)
  await enviarNotificacionWhatsApp({
    numero: '+51940267730',
    mensaje: `Nueva cotizacion de ${nombre}: ${cantidad} bloques → ${ubicacion}`
  });

  // 3. Generar link WhatsApp para cliente
  const whatsappURL = `https://wa.me/51940267730?text=...`;

  return {
    statusCode: 200,
    body: JSON.stringify({whatsappURL})
  };
};
```

```javascript
// functions/calcular-bloques.js
// Calcula cantidad de bloques segun medidas

exports.handler = async (event) => {
  const {largo, alto, ancho_bloque = 40, alto_bloque = 20} = JSON.parse(event.body);

  // Formula: (largo / ancho_bloque) * (alto / alto_bloque)
  const bloques_horizontal = Math.ceil((largo * 100) / ancho_bloque);
  const bloques_vertical = Math.ceil((alto * 100) / alto_bloque);
  const total = bloques_horizontal * bloques_vertical;

  // Agregar 5% extra por desperdicio
  const total_con_extra = Math.ceil(total * 1.05);

  return {
    statusCode: 200,
    body: JSON.stringify({
      bloques_necesarios: total,
      bloques_recomendados: total_con_extra,
      bloques_horizontal,
      bloques_vertical
    })
  };
};
```

---

## 🔄 FLUJO DE DATOS (v2.0)

### Escenario 1: Familia actualiza producto

```
Familia entra a Sanity Studio
    ↓
Edita producto (nombre, precio, foto)
    ↓
Guarda cambios
    ↓
Sanity API actualiza datos
    ↓
Frontend hace fetch a Sanity API
    ↓
Actualiza contenido en web (sin rebuild)
    ↓
Usuarios ven cambios instantaneamente
```

### Escenario 2: Cliente usa calculadora

```
Cliente ingresa medidas de su pared
    ↓
JS llama Netlify Function calcular-bloques
    ↓
Function calcula cantidad necesaria
    ↓
Retorna resultado con 5% extra
    ↓
Muestra resultado en web
    ↓
Boton "Solicitar Cotizacion" pre-llena datos
    ↓
Envia a WhatsApp con contexto
```

### Escenario 3: Cliente chatea con IA

```
Cliente abre widget de chat
    ↓
Escribe: "¿Tienen bloques de 10cm?"
    ↓
Chatbase IA busca en entrenamiento
    ↓
Responde: "Actualmente vendemos bloques de 15x20x40.
           ¿Te sirve esa medida para tu proyecto?"
    ↓
Cliente: "Si, necesito 300"
    ↓
IA: "Perfecto! Te conecto con nuestro equipo.
     [Boton WhatsApp con contexto]"
    ↓
Abre WhatsApp: "Cliente necesita 300 bloques de 15x20x40"
```

### Escenario 4: Cliente solicita cotizacion

```
Cliente llena formulario en web
    ↓
Frontend envia datos a Netlify Function
    ↓
Function guarda en Supabase
    ↓
Function notifica a familia por WhatsApp
    ↓
Function retorna link WhatsApp al cliente
    ↓
Cliente hace click, abre WhatsApp pre-llenado
    ↓
Familia ve notificacion + contexto completo
    ↓
Responde con cotizacion personalizada
```

---

## 🎨 ARQUITECTURA DE FRONTEND

### Estructura HTML (Semantica)

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <!-- Meta tags, SEO, Fonts -->
</head>
<body>
  <header> <!-- Navegacion fija --> </header>

  <main>
    <section id="hero"> <!-- Hero con CTA --> </section>
    <section id="caracteristicas"> <!-- 3 cards --> </section>
    <section id="productos"> <!-- Grid dinamico desde Sanity --> </section>
    <section id="calculadora"> <!-- Calculadora bloques --> </section>
    <section id="obras"> <!-- Galeria desde Sanity --> </section>
    <section id="nosotros"> <!-- Historia familiar --> </section>
    <section id="contacto"> <!-- Form + mapa --> </section>
  </main>

  <footer> <!-- Enlaces, contacto, copyright --> </footer>

  <!-- Scripts -->
  <script src="js/sanity-client.js"></script>
  <script src="js/main.js"></script>
  <script src="js/chatbot-loader.js"></script>
</body>
</html>
```

### Patron de carga de datos (Sanity)

```javascript
// js/sanity-client.js
import {createClient} from '@sanity/client';

const client = createClient({
  projectId: 'XXXX',
  dataset: 'production',
  useCdn: true,
  apiVersion: '2024-01-01'
});

// Obtener productos activos
async function cargarProductos() {
  const query = `*[_type == "producto" && activo == true]{
    nombre,
    descripcion,
    medidas,
    caracteristicas,
    "imagenURL": imagen.asset->url,
    precio
  }`;

  const productos = await client.fetch(query);
  renderizarProductos(productos);
}

// Obtener obras para galeria
async function cargarObras() {
  const query = `*[_type == "obra"] | order(fecha desc){
    titulo,
    descripcion,
    "imagenes": imagenes[].asset->url,
    ubicacion
  }[0...8]`; // Solo ultimas 8

  const obras = await client.fetch(query);
  renderizarCarrusel(obras);
}
```

### Patron de componentes reutilizables

```javascript
// js/componentes.js

// Componente: Tarjeta de producto
function crearTarjetaProducto(producto) {
  return `
    <div class="producto-card">
      <img src="${producto.imagenURL}" alt="${producto.nombre}">
      <h3>${producto.nombre}</h3>
      <p>${producto.descripcion}</p>
      <ul>
        ${producto.caracteristicas.map(c => `<li>${c}</li>`).join('')}
      </ul>
      <a href="https://wa.me/51940267730?text=Info%20${producto.nombre}"
         class="btn">Consultar Precio</a>
    </div>
  `;
}

// Componente: Slide de obra
function crearSlideObra(obra, index) {
  return `
    <div class="carousel__slide">
      <img src="${obra.imagenes[0]}" alt="${obra.titulo}">
      <div class="slide__info">
        <h4>${obra.titulo}</h4>
        <p>${obra.ubicacion}</p>
      </div>
    </div>
  `;
}
```

---

## 🔐 SEGURIDAD Y VALIDACIONES

### Validaciones actuales (v1.0)

**Formulario de contacto:**
- ✅ Campos obligatorios (HTML5 required)
- ✅ Validacion de telefono (type="tel")
- ⚠️ No hay sanitizacion server-side (no hay servidor)

### Validaciones futuras (v2.0)

**Sanity CMS:**
- ✅ Autenticacion obligatoria (email + password)
- ✅ Roles: Solo familia tiene acceso
- ✅ Validacion de campos (required, maxLength)

**Supabase:**
- ✅ Row Level Security (RLS) activado
- ✅ Solo lectura publica para productos
- ✅ Solo escritura autenticada para cotizaciones

**Netlify Functions:**
- ✅ Rate limiting (max 10 requests/minuto)
- ✅ Sanitizacion de inputs
- ✅ Validacion de datos antes de guardar

**Chatbase:**
- ✅ No expone datos sensibles
- ✅ No guarda conversaciones (GDPR compliant)

---

## 📈 ESCALABILIDAD

### Limitaciones actuales (v1.0)

| Aspecto | Limite actual | Escalabilidad |
|---------|--------------|---------------|
| Productos | Hardcodeados en HTML | Baja - requiere editar codigo |
| Fotos obras | 8 fijas | Baja - agregar mas requiere codigo |
| Idioma | Solo español | N/A - mercado local |
| Usuarios simultaneos | Ilimitado (CDN) | Alta - Netlify escala automatico |

### Mejoras de escalabilidad (v2.0)

| Aspecto | Solucion | Escalabilidad |
|---------|----------|---------------|
| Productos | Sanity CMS | Alta - familia agrega sin codigo |
| Fotos obras | Sanity CMS | Alta - ilimitadas |
| Cotizaciones | Supabase | Alta - miles de registros |
| Consultas IA | Chatbase | Alta - 1000+ chats/mes gratis |
| Trafico web | Netlify CDN | Alta - millones de visitas |

### Puntos de mejora para escalar

**Cuando agregar:**

1. **CDN para imagenes:** Si imagenes pesan mucho
   - Cloudinary o Imgix
   - Compresion automatica
   - Lazy loading

2. **Analytics:** Para ver trafico
   - Google Analytics 4
   - Plausible (privacy-friendly)
   - Ver que productos interesan mas

3. **A/B Testing:** Para optimizar conversiones
   - Probar diferentes CTAs
   - Diferentes posiciones de formulario

4. **Cache avanzado:** Si Sanity API es lento
   - Cache en Netlify Edge
   - ISR (Incremental Static Regeneration)

---

## 🧪 PUNTOS DE PRUEBA

### Criticos (v1.0)

1. **Formulario de contacto**
   - Validar que abre WhatsApp correctamente
   - Probar en diferentes navegadores
   - Probar en mobile

2. **Carrusel de obras**
   - Verificar que imagenes cargan
   - Probar navegacion (flechas, dots)
   - Responsive en mobile

3. **Menu mobile**
   - Hamburguesa funciona
   - Links cierran menu al hacer click
   - Smooth scroll funciona

### Criticos (v2.0)

1. **Integracion Sanity**
   - Cambio en Sanity aparece en web
   - Imagenes se cargan correctamente
   - Fallback si Sanity falla

2. **Chatbot IA**
   - Responde coherentemente
   - Deriva a WhatsApp cuando debe
   - No da informacion incorrecta

3. **Calculadora de bloques**
   - Formula correcta
   - Maneja casos extremos (medidas muy grandes)
   - Muestra resultados claros

4. **Sistema de notificaciones**
   - Familia recibe notificacion al llegar consulta
   - WhatsApp se abre con datos correctos
   - Se guarda en base de datos

---

## 🔮 ARQUITECTURA FUTURA (Fase 3+)

### Posibles expansiones

**Sistema de Pedidos Online:**
```
Cliente selecciona productos
    ↓
Calcula cantidad con calculadora
    ↓
Agrega al carrito
    ↓
Ingresa datos de entrega
    ↓
Confirma pedido
    ↓
Paga por transferencia/QR Yape
    ↓
Familia recibe pedido en dashboard
    ↓
Prepara entrega
```

**Blog de construccion:**
```
CMS (Sanity) con schema 'articulo'
    ↓
Familia escribe consejos (o IA ayuda)
    ↓
Publica en blog.norteblock.com
    ↓
SEO atrae trafico organico
    ↓
Posiciona como expertos
```

**App Mobile (muy futuro):**
```
React Native o Flutter
    ↓
Consume mismas APIs (Sanity, Supabase)
    ↓
Notificaciones push para familia
    ↓
Gestion de pedidos desde celular
```

---

**Ultima actualizacion:** 2025-01-28
**Mantenedor:** Juan Montenegro
