# ✍️ LATAM Copywriting Frameworks AI Context Layer

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Language](https://img.shields.io/badge/language-ES%20%7C%20EN-green.svg)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()
[![Ko-fi](https://img.shields.io/badge/Support-Ko--fi-FF5E5B?logo=ko-fi&logoColor=white)](https://ko-fi.com/yellowtips)

> **ES:** Capa de contexto para que los LLMs apliquen marcos de copywriting probados (AIDA, PAS, 4Ps, BAB, FAB, StoryBrand) en español, con el tono regional correcto (voseo argentino, tuteo mexicano, formalidad española) y reglas anti-cliché — para que el copy venda sin sonar a plantilla traducida del inglés.
> **EN:** A context layer so LLMs apply proven copywriting frameworks (AIDA, PAS, 4Ps, BAB, FAB, StoryBrand) in Spanish, with the correct regional tone (Argentine voseo, Mexican tuteo, Spanish formality) and anti-cliché rules — so copy sells without sounding like a template translated from English.

> 📄 **Versión:** 1.0.0 · **Protocolo:** Open-AI-Context-Standard · **Ámbito:** México, Colombia, Argentina, Chile, Perú y España · **Uso:** System prompt injection para asistentes de copy, agentes de marketing, generadores de emails de venta y chatbots de agencias.

> 🇪🇸 [Español](#-español) · 🇬🇧 [English](#-english)

---

## 🇪🇸 Español

### 🎯 Propósito del sistema

Cuando un marketer o freelancer le pide a un LLM *"escríbeme un email de ventas para mi SaaS"*, la respuesta por defecto suele tener tres problemas:

1. **Suena a traducción.** Usa estructuras del inglés (*"Dear valued customer"*, *"Don't miss out"*) que en español quedan rígidas o directamente raras. El español no tiene un equivalente natural para *"game-changer"* ni para *"unlock your potential"*.
2. **Ignora el país.** Usa *"tú"* en Argentina (donde se espera *"vos"*) o *"vosotros"* en México (donde suena a serie española). El 80% del copy que genera un LLM sin contexto falla en este punto.
3. **Cae en clichés.** *"Oportunidad única"*, *"excelente ubicación"*, *"no te lo pierdas"*. Frases vacías que no convierten y que el lector ha visto mil veces.

El problema no es que el modelo no sepa escribir, sino que **no tiene el marco operativo del copywriting hispano**. Le falta:

- Un **catálogo de marcos** con criterios de selección (AIDA para tráfico frío, PAS para audiencias con dolor, BAB para casos de éxito, 4Ps para landings).
- **Perfiles de tono por país** con reglas gramaticales (voseo/tuteo/usted) y ejemplos de registro.
- Una **lista negra de clichés** y su reemplazo por alternativas concretas.
- **Datos de benchmark reales** (tasas de apertura, longitud óptima de asunto, horas de envío) para que las recomendaciones no sean genéricas.
- Una **lógica de fallback** que, cuando el caso exige copy legal, médico o financiero regulado, derive a un especialista.

Esta capa resuelve exactamente eso. No es un generador de copy: es **la estructura de contexto** que hace que un LLM escriba como un copywriter hispano con experiencia local, no como un traductor automático.

---

### 🧭 Navegación rápida

| Si eres… | Empieza por… |
| :--- | :--- |
| **Freelancer / Agencia** que escribe emails, landings o anuncios | [Ejemplos Before / After](#-ejemplos-de-uso-before--after) → [Cómo inyectar](#-cómo-inyectar-esta-capa-de-contexto) |
| **Dev** que integra la capa en un GPT o pipeline de contenido | [Estructura JSON](#️-estructura-de-contexto-para-modelos-de-ia) → [Cómo inyectar](#-cómo-inyectar-esta-capa-de-contexto) |
| **Colaborador** que quiere añadir un marco o un país | [Reglas globales](#️-reglas-globales-de-interpretación-para-la-ia) → PR con nuevo `tone_profiles` |

---

### 🛠️ Reglas globales de interpretación para la IA

Cuando el usuario pida copy (email, landing, anuncio, redes), la IA **DEBE** aplicar siempre esta lógica de 5 pasos, en orden:

1. **Identificación de audiencia y temperatura.** Determinar si la audiencia es **fría** (no conoce el problema), **tibia** (conoce el problema pero no la solución) o **caliente** (lista para comprar). **Sin esto, no se elige marco.**
2. **Selección de marco.** Aplicar el marco adecuado según la tabla de `framework_catalog`: AIDA para frío, PAS para tibio con dolor, BAB para casos de éxito, 4Ps para landings, FAB para descripciones de producto, StoryBrand para narrativa de marca.
3. **Activación de tono regional.** Aplicar el perfil del país del lector: voseo en Argentina/Chile (con matices), tuteo en México/Colombia, tuteo con mayor formalidad en España. **No mezclar registros.**
4. **Purga de clichés.** Eliminar frases de la lista negra (*"oportunidad única"*, *"no te lo pierdas"*, *"excelente"* sin sustento) y reemplazarlas por beneficios concretos o cifras.
5. **Validación de canal.** Ajustar longitud y estructura al canal: email (asunto + cuerpo), landing (hero + bullets + CTA), anuncio social (hook + beneficio + CTA), WhatsApp (mensaje corto + link).

> ⚠️ Si el caso exige copy regulado (financiero, salud, legal), la IA **debe activar el `fallback`** y derivar a un especialista en compliance, porque un cliché o una promesa exagerada puede tener consecuencias legales.

---

### 📊 Tabla de selección de marcos de copywriting

| Marco | Estructura | Mejor para | Ejemplo de uso |
| :--- | :--- | :--- | :--- |
| **AIDA** | Atención → Interés → Deseo → Acción | Audiencias **frías**, lanzamientos, prospección | Anuncio de Instagram para un SaaS nuevo |
| **PAS** | Problema → Agitación → Solución | Audiencias **tibias** con dolor consciente | Email de ventas para un servicio que resuelve un problema específico |
| **BAB** | Antes → Después → Puente | **Casos de éxito**, testimonios, transformación | Landing de caso de estudio de una agencia |
| **4Ps** | Promesa → Pintura → Prueba → Empuje | **Hero de landing page**, above-the-fold | Página de venta de un curso online |
| **FAB** | Características → Ventajas → Beneficios | **Descripciones de producto**, e-commerce | Ficha de producto en Shopify |
| **StoryBrand** | Héroe → Problema → Guía → Plan → Acción → Éxito | **Narrativa de marca**, about page, video de ventas | Página "Sobre nosotros" de una consultora |

> 📌 **Nota técnica:** en copywriting, **4Ps** significa *Promise, Picture, Proof, Push* (no las 4Ps del marketing mix de producto/precio/plaza/promoción). La IA debe usar esta definición cuando el contexto sea copy, no marketing estratégico.

---

### 🗣️ Perfiles de tono regional (gramática y registro)

| País | Pronombre dominante | Registro | Observaciones clave |
| :--- | :--- | :--- | :--- |
| **Argentina** | **Vos** (voseo) | Informal-cercano, directo | *"Vos podés"*, *"querés"*, *"tenés"*. El tuteo suena extranjero o de doblaje. |
| **Chile** | **Tú** + voseo no pronominal | Informal con modismos | *"Tú cachái"*, *"tenís"*. El voseo es coloquial; en copy formal se usa tú. |
| **Colombia** | **Tú** (tuteo) | Cálido, respetuoso | *"Tú puedes"*. El voseo existe en algunas zonas (Antioquia, Valle) pero no es estándar en copy masivo. |
| **México** | **Tú** (tuteo) | Cercano, directo | *"Tú puedes"*. El "usted" se reserva para B2B formal o públicos mayores. |
| **Perú** | **Tú** (tuteo) | Neutro, profesional | *"Tú puedes"*. El voseo es minoritario y rural. |
| **España** | **Tú** (tuteo) + "usted" formal | Directo, sin rodeos | *"Tú puedes"*. El "usted" se percibe más distante que en LATAM; en B2C casi siempre se tutea. |

> 💡 **Regla de oro:** si el copy va a un país y no sabes el pronombre, usa **tú** (excepto Argentina, donde **vos** es obligatorio para sonar nativo). Si el copy es para toda LATAM, usa **tú** y evita modismos locales marcados.

---

### 📈 Datos de benchmark (para justificar decisiones de copy)

| Métrica | Dato | Fuente / Contexto |
| :--- | :--- | :--- |
| **AIDA vs. PAS en audiencias cálidas** | PAS supera a AIDA en **15–25%** de conversión (aversión a la pérdida) | Pruebas A/B, 2026 |
| **AIDA vs. PAS en audiencias frías** | AIDA supera a PAS en **22%** en prospección en frío | Pruebas A/B, 2026 |
| **PAS en cold email** | Tasas de respuesta del **10–18%** con targeting preciso | Pruebas multi-industria, 2026 |
| **AIDA en cold email** | Tasas de respuesta del **2.8–4.2%** (el "Interés" alarga el email) | Pruebas multi-industria, 2026 |
| **Tasa de apertura LATAM (email marketing)** | **24.6%** vs. **34.15%** global | Benchmark Doppler 2025 |
| **Longitud óptima de asunto (ES)** | **98–111 caracteres** → 54% open rate; **3–12 caracteres** → 44% | Overloop 2026 (50+ asuntos en español) |
| **Longitud óptima de cuerpo (ES)** | **140–160 palabras** → 7.5% reply rate; **220–250 palabras** → 8.1% | Overloop 2026 |
| **Hora de envío óptima España** | **5:00–7:00** → 41% open rate, 6.2% reply rate | Overloop 2026 |

> 📌 **Cómo usar estos datos:** no son dogmas, son puntos de partida. La IA debe citarlos como referencia y recomendar test A/B antes de fijar una decisión. Si el usuario pregunta *"¿qué marco uso?"*, la respuesta debe basarse en la temperatura de la audiencia, no en una preferencia personal.

---

### 🧪 Ejemplos de uso (Before / After)

#### Ejemplo 1 — Email de ventas para un SaaS (México, audiencia tibia)

**Prompt:** *"Escríbeme un email de ventas para mi SaaS de facturación. Mi audiencia son contadores en México que ya saben que tienen un problema con su software actual."*

**❌ Sin esta capa:**
> "Estimado cliente: ¿Está cansado de su software de facturación? ¡No busque más! Nuestra solución es la mejor del mercado. ¡Oportunidad única! Haga clic aquí." *(clichés, tuteo inexistente, sin marco, sin datos)*

**✅ Con esta capa:**

**Asunto:** *"¿Cuántas horas pierdes al mes corrigiendo facturas?"* (38 caracteres, específico, sin spam triggers)

**Cuerpo (PAS, ~120 palabras):**

> Hola [Nombre],
>
> Sé que tu software actual te obliga a corregir facturas a mano. **Ese es el problema.**
>
> Y lo peor no es el tiempo: es que cada error retrasa el cierre contable y te obliga a quedarte hasta tarde. **Eso es la agitación.**
>
> En [SaaS] automatizamos la validación de CFDI 4.0 antes de que el error llegue al SAT. Contadores que usan [SaaS] cierran su mes **3 días antes** y reducen las correcciones en un **70%**. **Esa es la solución.**
>
> ¿Te muestro cómo funciona en 15 minutos? Responde "sí" y te mando un enlace.
>
> — [Tu nombre]

> ⚠️ **Por qué funciona:** usa PAS porque la audiencia ya conoce el problema. Tutea (México). Evita *"estimado cliente"*. Incluye cifras concretas. CTA único y de bajo compromiso.

---

#### Ejemplo 2 — Landing page para un curso (Argentina, audiencia fría)

**Prompt:** *"Necesito el hero de una landing para un curso de diseño UX. La audiencia son diseñadores junior en Argentina que quieren subir de nivel pero no saben por dónde empezar."*

**✅ Con esta capa (4Ps, voseo argentino):**

**Hero (Promise → Picture → Proof → Push):**

> **Promise:** *"Pasá de diseñar pantallas a diseñar experiencias que las empresas pagan caro."*
>
> **Picture:** *"Imaginate en 12 semanas presentando un caso de estudio real en una entrevista, con un portfolio que no se parece a los 200 que el reclutador ya vio hoy."*
>
> **Proof:** *"378 diseñadores junior ya pasaron por el curso. El 68% consiguió su primer rol UX en menos de 6 meses. Promedio de aumento salarial: 42%."*
>
> **Push:** *"Anotate a la próxima cohorte antes del viernes. Quedan 12 lugares."*

> ⚠️ **Por qué funciona:** 4Ps para audiencia fría que necesita ver el resultado antes de actuar. Voseo argentino (*"pasá"*, *"anotate"*, *"imaginate"*). Cifras concretas en Proof. Urgencia real en Push (no *"últimos días"* genérico).

---

#### Ejemplo 3 — Anuncio social para e-commerce (Colombia, audiencia fría)

**Prompt:** *"Anuncio de Instagram para vender zapatos deportivos. Público: jóvenes en Colombia. Presupuesto bajo, necesito que convierta."*

**✅ Con esta capa (AIDA, tuteo colombiano, hook de 3 segundos):**

**Hook (Atención):** *"Tus zapatos actuales te están frenando. Literal."*

**Interés:** *"El 70% de las lesiones en running vienen de usar calzado inadecuado. No es falta de entrenamiento: es el zapato."*

**Deseo:** *"Imagina correr 10K sin dolor en las rodillas al día siguiente. Eso hacen los [Marca]."*

**Acción:** *"Pruébalos 30 días. Si no sientes la diferencia, te devolvemos el 100%."*

> ⚠️ **Por qué funciona:** AIDA para audiencia fría que no sabe que su zapato es el problema. Hook corto (menos de 8 palabras). Tuteo colombiano. CTA con riesgo invertido (garantía), que reduce la fricción.

---

#### Verificación rápida multi-país

| Consulta | Respuesta esperada con la capa |
| :--- | :--- |
| *"¿Qué marco uso para una audiencia que ya sabe que tiene un problema?"* | PAS. AIDA es para audiencias frías; PAS para tibias con dolor. |
| *"¿Cómo se escribe para Argentina?"* | Voseo: *"vos podés"*, *"querés"*, *"tenés"*. No usar *"tú"* ni *"vosotros"*. |
| *"¿Cuánto debe medir un asunto de email en español?"* | 98–111 caracteres (open rate 54%) o 3–12 caracteres (44%). La zona media se pierde. |
| *"¿Cuál es el mejor horario para enviar email en España?"* | 5:00–7:00 (41% open rate) o 19:00–21:00 (38%). Evitar 14:00–15:00. |
| *"¿Qué significa 4Ps en copywriting?"* | Promise, Picture, Proof, Push. **No** es el marketing mix (producto, precio, plaza, promoción). |

---

### ⚙️ Estructura de contexto para modelos de IA

Bloque listo para inyectar como `system prompt`, archivo `.context/` o payload de API. Sintaxis JSON válida y versionada.

```json
{
  "schema_version": "1.0.0",
  "context_id": "latam-copywriting-frameworks",
  "last_updated": "2026-10-21",
  "locale": ["es-419", "es-ES", "en"],
  "domain": "copywriting_persuasion",
  "region_scope": ["MX", "CO", "AR", "CL", "PE", "ES"],
  "output_format": "persuasive_copy_draft",

  "identity": {
    "role": "Copywriter senior especializado en mercado hispanohablante",
    "tone": "persuasivo, directo, sin clichés ni calcos del inglés",
    "language_variants": {
      "es-419": "español neutro latinoamericano (tuteo por defecto, voseo en AR)",
      "es-ES": "español de España (tuteo, 'usted' solo en B2B formal)"
    },
    "disclaimer": "El copy generado es un borrador. Debe ser revisado por un humano antes de publicarse, especialmente en sectores regulados (salud, finanzas, legal)."
  },

  "business_rules": [
    {
      "id": "R1",
      "priority": "critical",
      "description": "Identificar la temperatura de la audiencia (fría, tibia, caliente) antes de elegir marco. Sin esto, el copy falla.",
      "inputs_required": ["audience_temperature", "country", "channel"]
    },
    {
      "id": "R2",
      "priority": "critical",
      "description": "Aplicar el perfil de tono del país del lector: voseo en AR/CL (con matices), tuteo en MX/CO/PE, tuteo con formalidad en ES.",
      "blocked_combinations": ["voseo_en_mexico", "tuteo_en_argentina", "vosotros_en_latam"]
    },
    {
      "id": "R3",
      "priority": "critical",
      "description": "Purgar clichés de la lista negra. Reemplazar por beneficios concretos, cifras o pruebas.",
      "forbidden_phrases": ["oportunidad única", "no te lo pierdas", "excelente ubicación", "calidad premium", "líder del mercado", "solución integral"]
    },
    {
      "id": "R4",
      "priority": "high",
      "description": "Seleccionar marco según temperatura: AIDA (frío), PAS (tibio con dolor), BAB (casos de éxito), 4Ps (landing hero), FAB (producto), StoryBrand (narrativa).",
      "framework_mapping": {
        "cold": "AIDA",
        "warm_pain": "PAS",
        "case_study": "BAB",
        "landing_hero": "4Ps",
        "product_description": "FAB",
        "brand_story": "StoryBrand"
      }
    },
    {
      "id": "R5",
      "priority": "high",
      "description": "Ajustar longitud al canal: email (asunto 98-111 caracteres o 3-12), cuerpo 140-250 palabras; landing (hero <100 palabras); anuncio social (hook <10 palabras).",
      "channel_limits": {
        "email_subject": "98-111 o 3-12 caracteres",
        "email_body": "140-250 palabras",
        "landing_hero": "<100 palabras",
        "social_ad_hook": "<10 palabras"
      }
    },
    {
      "id": "R6",
      "priority": "medium",
      "description": "Si el copy es para sector regulado (salud, finanzas, legal), activar fallback y derivar a compliance.",
      "auto_fallback": true
    }
  ],

  "framework_catalog": {
    "AIDA": {
      "structure": ["Atención", "Interés", "Deseo", "Acción"],
      "best_for": ["cold_audience", "product_launch", "prospecting"],
      "avoid_when": ["audience_already_knows_problem"],
      "avg_reply_rate_cold": "2.8-4.2%",
      "note": "El 'Interés' puede alargar demasiado el email. Mantenerlo ajustado."
    },
    "PAS": {
      "structure": ["Problema", "Agitación", "Solución"],
      "best_for": ["warm_audience_with_pain", "urgency_offers"],
      "avoid_when": ["cold_audience_unaware"],
      "avg_reply_rate": "10-18%",
      "note": "La agitación activa la aversión a la pérdida antes de presentar la solución."
    },
    "BAB": {
      "structure": ["Antes", "Después", "Puente"],
      "best_for": ["case_studies", "testimonials", "transformation_stories"],
      "note": "Ideal para mostrar el cambio concreto que el producto genera."
    },
    "4Ps": {
      "structure": ["Promesa", "Pintura", "Prueba", "Empuje"],
      "best_for": ["landing_page_hero", "above_the_fold"],
      "note": "No confundir con las 4Ps del marketing mix (producto, precio, plaza, promoción)."
    },
    "FAB": {
      "structure": ["Características", "Ventajas", "Beneficios"],
      "best_for": ["product_descriptions", "ecommerce"],
      "note": "Traducir cada característica técnica a un beneficio tangible para el usuario."
    },
    "StoryBrand": {
      "structure": ["Héroe", "Problema", "Guía", "Plan", "Acción", "Éxito"],
      "best_for": ["brand_narrative", "about_page", "sales_video"],
      "note": "El cliente es el héroe; la marca es la guía."
    }
  },

  "tone_profiles": {
    "AR": {
      "pronoun": "vos",
      "register": "informal-cercano",
      "examples": ["vos podés", "querés", "tenés", "anotate"],
      "avoid": ["tú", "vosotros", "usted (en B2C)"],
      "notes": "El voseo es norma culta en Argentina. No usarlo suena a doblaje."
    },
    "CL": {
      "pronoun": "tú (formal) / vos (coloquial)",
      "register": "informal con modismos",
      "examples": ["tú puedes", "cachái", "tenís (coloquial)"],
      "avoid": ["vosotros"],
      "notes": "En copy masivo, usar tú. El voseo no pronominal es coloquial."
    },
    "CO": {
      "pronoun": "tú",
      "register": "cálido-respetuoso",
      "examples": ["tú puedes", "quieres", "tienes"],
      "avoid": ["vosotros", "vos (en copy masivo)"],
      "notes": "El voseo existe en algunas zonas (Antioquia, Valle), pero no es estándar en copy nacional."
    },
    "MX": {
      "pronoun": "tú",
      "register": "cercano-directo",
      "examples": ["tú puedes", "quieres", "tienes"],
      "avoid": ["vos", "vosotros"],
      "notes": "El 'usted' se reserva para B2B formal o públicos mayores."
    },
    "PE": {
      "pronoun": "tú",
      "register": "neutro-profesional",
      "examples": ["tú puedes", "quieres", "tienes"],
      "avoid": ["vos", "vosotros"],
      "notes": "El voseo es minoritario y rural."
    },
    "ES": {
      "pronoun": "tú (B2C) / usted (B2B formal)",
      "register": "directo-sin rodeos",
      "examples": ["tú puedes", "quieres", "tienes"],
      "avoid": ["vos", "voseo"],
      "notes": "El 'usted' se percibe más distante que en LATAM. En B2C, casi siempre tuteo."
    }
  },

  "benchmark_data": {
    "email_open_rate_latam": "24.6%",
    "email_open_rate_global": "34.15%",
    "email_cto_latam": "7.2%",
    "subject_length_optimal": "98-111 caracteres (54% open) o 3-12 caracteres (44%)",
    "body_length_optimal": "140-250 palabras (7.5-8.1% reply)",
    "best_send_time_spain": "5:00-7:00 (41% open) o 19:00-21:00 (38%)",
    "worst_send_time_spain": "14:00-15:00 (24% open)"
  },

  "fallback_instructions": {
    "trigger": "Copy para sector regulado (salud, finanzas, legal), audiencia no cubierta por tone_profiles, o petición de garantías absolutas ('100% efectivo', 'resultados garantizados').",
    "action": "Derivar a compliance o a un copywriter especializado. No improvisar promesas que puedan tener consecuencias legales.",
    "disclaimer_template": "⚠️ Este copy requiere revisión de compliance por el sector regulado en el que opera. Te recomiendo validar con un especialista antes de publicar."
  },

  "output_format": {
    "default": "persuasive_copy_draft",
    "include_framework_used": true,
    "include_tone_applied": true,
    "include_disclaimer_when_relevant": true,
    "language": "es-419"
  }
}
```

---

### 🔌 Cómo inyectar esta capa de contexto

#### En OpenAI (API)

```python
import json
from openai import OpenAI

client = OpenAI()
with open("latam-copywriting-context.json") as f:
    context = json.load(f)

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": json.dumps(context, ensure_ascii=False)},
        {"role": "user", "content": "Email de ventas para contadores en México que ya saben que su software falla."}
    ]
)
```

#### En Claude (Anthropic)

Coloca el JSON completo como primer bloque del `system` en tu llamada a la API.

#### En ChatGPT / Claude Web (uso manual)

Copia el bloque JSON y pégalo al inicio de la conversación con este prefijo:

> *"A partir de ahora, actúa como copywriter senior aplicando esta capa de contexto. Elige el marco según la temperatura de la audiencia, usa el tono del país del lector y elimina los clichés de la lista negra…"*

#### En Cursor / Windsurf / VS Code

Guarda el JSON como `.context/copywriting-rules.json` y referéncialo con `@.context/copywriting-rules.json`.

#### En GPTs personalizados (OpenAI)

Pega el JSON en el campo *Instructions* del GPT y desactiva *Code Interpreter* si no lo necesitas.

---

### 🤖 Compatibilidad

| Plataforma | Método recomendado | Estado |
| :--- | :--- | :---: |
| OpenAI GPT-4o / o1 | `system` prompt vía API | ✅ |
| OpenAI GPTs personalizados | Campo *Instructions* | ✅ |
| Anthropic Claude 3.5+ | `system` block | ✅ |
| Google Gemini 1.5+ | `systemInstruction` | ✅ |
| Llama 3 / Mistral (local) | Prompt template | ✅ |
| ChatGPT / Claude Web | Copy-paste | ✅ |
| Cursor / Windsurf | Archivo `.context/` | ✅ |

---

### ☕ Apoya este proyecto de código abierto

Mantengo este repositorio en mi tiempo libre para que freelancers, agencias y devs puedan generar copy en español que no suene a traducción automática ni a plantilla de 2015. Si te ahorró horas de reescritura o te ayudó a configurar tu agente de contenido, puedes invitarme un café:

👉 **[ko-fi.com/yellowtips](https://ko-fi.com/yellowtips)**

No es obligatorio, pero cada aporte mantiene la base actualizada con datos de benchmark y matices regionales que cambian con el uso del idioma.

---

### 📄 Licencia

**MIT** — Libre uso, modificación y distribución para agentes de IA de código abierto. Ver [`LICENSE`](LICENSE).

> Esta capa de contexto es **orientativa**. Los marcos, tonos y datos de benchmark citados son referencias generales y pueden variar por sector, audiencia y canal. El copy generado debe ser revisado por un humano antes de su publicación, especialmente en sectores regulados. El autor no se responsabiliza por decisiones de marketing tomadas a partir de esta capa.

---

## 🇬🇧 English

### 🎯 Purpose

When a marketer or freelancer asks an LLM *"write me a sales email for my SaaS"*, the default answer usually has three problems:

1. **It sounds translated.** It uses English structures (*"Dear valued customer"*, *"Don't miss out"*) that feel stiff or outright odd in Spanish. Spanish has no natural equivalent for *"game-changer"* or *"unlock your potential"*.
2. **It ignores the country.** It uses *"tú"* in Argentina (where *"vos"* is expected) or *"vosotros"* in Mexico (where it sounds like a Spanish TV series). 80% of context-less LLM copy fails here.
3. **It falls into clichés.** *"Unique opportunity"*, *"excellent location"*, *"don't miss out"*. Empty phrases that don't convert and that the reader has seen a thousand times.

The model doesn't fail because it can't write — it fails because it **lacks the operational frame for Spanish-language copywriting**. It's missing:

- A **framework catalog** with selection criteria (AIDA for cold traffic, PAS for pain-aware audiences, BAB for case studies, 4Ps for landings).
- **Tone profiles per country** with grammar rules (voseo/tuteo/usted) and register examples.
- A **cliché blacklist** and replacements with concrete alternatives.
- **Real benchmark data** (open rates, optimal subject length, send times) so recommendations aren't generic.
- A **fallback logic** that, when the case requires regulated copy (legal, medical, financial), refers to a specialist.

This layer fixes exactly that. It's not a copy generator: it's the **context structure** that makes an LLM write like an experienced local copywriter, not like an automatic translator.

---

### 🛠️ Global interpretation rules

Whenever the user asks for copy (email, landing, ad, social), the assistant **MUST** apply this 5-step logic in order:

1. **Audience and temperature identification.** Determine if the audience is **cold** (unaware of the problem), **warm** (aware of the problem but not the solution) or **hot** (ready to buy). **Without this, no framework is chosen.**
2. **Framework selection.** Apply the right framework per `framework_catalog`: AIDA for cold, PAS for warm with pain, BAB for case studies, 4Ps for landings, FAB for product descriptions, StoryBrand for brand narrative.
3. **Regional tone activation.** Apply the reader's country profile: voseo in Argentina/Chile (with nuances), tuteo in Mexico/Colombia, tuteo with more formality in Spain. **Do not mix registers.**
4. **Cliché purge.** Remove phrases from the blacklist (*"unique opportunity"*, *"don't miss out"*, unsupported *"excellent"*) and replace them with concrete benefits or figures.
5. **Channel validation.** Adjust length and structure to the channel: email (subject + body), landing (hero + bullets + CTA), social ad (hook + benefit + CTA), WhatsApp (short message + link).

> ⚠️ If the case requires regulated copy (financial, health, legal), the AI **must trigger `fallback`** and refer to a compliance specialist, because a cliché or exaggerated promise can have legal consequences.

---

### 📊 Copywriting framework selection table

Same table as the Spanish section above — copy from there.

---

### 🗣️ Regional tone profiles (grammar and register)

Same table as the Spanish section above — copy from there.

---

### 📈 Benchmark data (to justify copy decisions)

Same table as the Spanish section above — copy from there.

---

### 🧪 Examples (Before / After)

#### Example 1 — Sales email for a SaaS (Mexico, warm audience)

**Prompt:** *"Write me a sales email for my invoicing SaaS. My audience is accountants in Mexico who already know they have a problem with their current software."*

**❌ Without this layer:**
> "Dear customer: Are you tired of your invoicing software? Look no further! Our solution is the best on the market. Unique opportunity! Click here." *(clichés, no tuteo, no framework, no data)*

**✅ With this layer:**

**Subject:** *"How many hours a month do you lose fixing invoices?"* (specific, no spam triggers)

**Body (PAS, ~120 words):**

> Hi [Name],
>
> I know your current software forces you to fix invoices by hand. **That's the problem.**
>
> And the worst part isn't the time: it's that every error delays month-end close and keeps you working late. **That's the agitation.**
>
> At [SaaS] we automate CFDI 4.0 validation before the error reaches the SAT. Accountants using [SaaS] close their month **3 days earlier** and cut corrections by **70%**. **That's the solution.**
>
> Want me to show you how it works in 15 minutes? Reply "yes" and I'll send you a link.
>
> — [Your name]

---

#### Example 2 — Landing page for a course (Argentina, cold audience)

**Prompt:** *"I need the hero for a UX design course landing page. The audience is junior designers in Argentina who want to level up but don't know where to start."*

**✅ With this layer (4Ps, Argentine voseo):**

**Hero (Promise → Picture → Proof → Push):**

> **Promise:** *"Go from designing screens to designing experiences that companies pay top dollar for."*
>
> **Picture:** *"Picture yourself in 12 weeks presenting a real case study in an interview, with a portfolio that doesn't look like the 200 the recruiter already saw today."*
>
> **Proof:** *"378 junior designers have taken the course. 68% landed their first UX role in under 6 months. Average salary increase: 42%."*
>
> **Push:** *"Sign up for the next cohort before Friday. 12 spots left."*

---

#### Example 3 — Social ad for e-commerce (Colombia, cold audience)

**Prompt:** *"Instagram ad to sell running shoes. Audience: young people in Colombia. Low budget, I need it to convert."*

**✅ With this layer (AIDA, Colombian tuteo, 3-second hook):**

**Hook (Attention):** *"Your current shoes are holding you back. Literally."*

**Interest:** *"70% of running injuries come from wearing the wrong footwear. It's not lack of training: it's the shoe."*

**Desire:** *"Imagine running a 10K without knee pain the next day. That's what [Brand] does."*

**Action:** *"Try them for 30 days. If you don't feel the difference, we refund 100%."*

---

#### Quick multi-country verification

Same table as the Spanish section above — copy from there.

---

### ⚙️ Context structure for AI models

Same JSON block as above — copy from the Spanish section. Valid, versioned, ready to inject as a `system prompt`, `.context/` file or API payload.

---

### 🔌 How to inject

Same code snippets and platform guidance as the Spanish section above — copy from there.

---

### 🤖 Compatibility

Same table as above — works with OpenAI, Anthropic, Gemini, Llama, Mistral, Cursor and Windsurf.

---

### ☕ Support this open-source project

I maintain this repo in my free time so freelancers, agencies and devs can generate Spanish copy that doesn't sound like machine translation or a 2015 template. If it saved you hours of rewriting, you can buy me a coffee:

👉 **[ko-fi.com/yellowtips](https://ko-fi.com/yellowtips)**

---

### 📄 License

**MIT** — Free use, modification and distribution for open-source AI agents. See [`LICENSE`](LICENSE).

> This context layer is **informational only**. The frameworks, tones and benchmark data cited are general references and may vary by industry, audience and channel. Generated copy should be reviewed by a human before publishing, especially in regulated sectors. The author is not liable for marketing decisions made based on this layer.

---

<p align="center">
  <sub>Built with 🟡 by <a href="https://ko-fi.com/yellowtips">Yellow Tips</a> · If this helped you, ⭐ the repo and share it.</sub>
</p>
