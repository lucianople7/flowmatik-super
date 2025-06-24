# 🚀 Flowmatik Professional Backend

Backend profesional con 8 agentes de IA especializados, integración con Doubao 1.5-pro y sistema de memoria eterna.

## ✨ Características

- **8 Agentes de IA Especializados** - Cada uno con personalidad y expertise únicos
- **Integración Doubao 1.5-pro** - Modelo de IA avanzado via 302.AI
- **Sistema de Memoria Eterna** - Recordar conversaciones y contexto de usuarios
- **API RESTful Completa** - Endpoints para chat, generación y administración
- **Optimizado para Cloudflare Workers** - Deploy global con latencia <50ms
- **CORS Configurado** - Listo para integración frontend

## 🤖 Agentes Disponibles

| Agente | Rol | Especialidad |
|--------|-----|--------------|
| **FLOWI CEO** | Leadership & Strategy | Estrategia empresarial, liderazgo |
| **TREND RESEARCHER** | Trending Topics Analysis | Análisis de tendencias, investigación |
| **HOOK CREATOR** | Engaging Hook Generator | Copywriting, engagement |
| **EDITOR PRO** | Professional Video Editor | Edición de video, storytelling |
| **THUMBNAIL WIZARD** | Thumbnail Design Expert | Diseño gráfico, optimización CTR |
| **OPTIMIZER** | Performance Optimization | SEO, analytics, conversiones |
| **CONTENT STRATEGIST** | Content Strategy Specialist | Estrategia de contenido, KPIs |
| **DATA MASTER** | Advanced Analytics Expert | Big data, machine learning |

## 🛠️ Instalación y Deploy

### Requisitos Previos

- Cuenta en [Cloudflare](https://dash.cloudflare.com/)
- API Key de [302.AI](https://302.ai/) para Doubao 1.5-pro
- Repositorio en GitHub

### Configuración

1. **Subir archivos a GitHub:**
   ```bash
   # Subir todos los archivos de este proyecto a tu repositorio
   ```

2. **Configurar Cloudflare Workers:**
   - Ve a Workers & Pages en Cloudflare
   - Conecta tu repositorio de GitHub
   - Configura las variables de entorno

3. **Variables de Entorno Requeridas:**
   ```toml
   AI_302_API_KEY = "tu-api-key-de-302ai"
   ```

4. **Variables Opcionales:**
   ```toml
   FLOWMATIK_MEMORY = "tu-kv-namespace" # Para memoria persistente
   ```

## 📡 API Endpoints

### Información General

```http
GET /
GET /health
GET /api/test
```

### Agentes

```http
GET /api/agents
POST /api/agents/:agentId/chat
POST /api/agents/:agentId/generate
```

### Terminal Administrativo

```http
POST /api/terminal/chat
GET /api/terminal/status
GET /api/terminal/analytics
GET /api/terminal/memory/:userId?
```

## 💬 Ejemplos de Uso

### Chat con Agente

```javascript
const response = await fetch('https://tu-worker.workers.dev/api/agents/flowi-ceo/chat', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    message: "¿Cuál es la mejor estrategia para hacer viral un video?",
    userId: "usuario123"
  })
});

const data = await response.json();
console.log(data.response);
```

### Generar Contenido

```javascript
const response = await fetch('https://tu-worker.workers.dev/api/agents/hook-creator/generate', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    prompt: "Crear 5 hooks para un video sobre productividad",
    userId: "usuario123",
    context: {
      platform: "TikTok",
      audience: "emprendedores"
    }
  })
});

const data = await response.json();
console.log(data.content);
```

## 🔧 Configuración Avanzada

### KV Storage para Memoria Persistente

1. Crear KV Namespace en Cloudflare:
   ```bash
   wrangler kv:namespace create "FLOWMATIK_MEMORY"
   ```

2. Añadir al `wrangler.toml`:
   ```toml
   [[kv_namespaces]]
   binding = "FLOWMATIK_MEMORY"
   id = "tu-kv-namespace-id"
   ```

### Personalizar Agentes

Edita el objeto `AI_AGENTS` en `src/index.js` para:
- Añadir nuevos agentes
- Modificar personalidades
- Cambiar especialidades

## 📊 Monitoreo y Analytics

### Métricas Disponibles

- Requests por agente
- Tiempo de respuesta promedio
- Uso de tokens
- Análisis de costos
- Estado del sistema

### Logs y Debugging

```javascript
// Ver logs en tiempo real
console.log('Cloudflare Workers Logs');

// Endpoint de estado
GET /api/terminal/status
```

## 💰 Costos y Performance

### Ventajas Económicas

- **94% más barato** que GPT-4
- **$10-20/mes** costo estimado
- **Doubao 1.5-pro:** $0.11 input / $0.28 output por 1M tokens

### Performance

- **Latencia:** <50ms global
- **Uptime:** 99.9% garantizado
- **Escalabilidad:** Millones de requests
- **Edge Computing:** 200+ ubicaciones

## 🔒 Seguridad

- Variables de entorno seguras
- CORS configurado
- Validación de inputs
- Manejo de errores robusto
- Rate limiting (configurable)

## 🚀 Roadmap

- [ ] Integración con más modelos de IA
- [ ] Sistema de autenticación
- [ ] Rate limiting avanzado
- [ ] Webhooks para notificaciones
- [ ] Dashboard de analytics
- [ ] API de administración completa

## 📞 Soporte

Para soporte técnico o consultas:
- **Email:** soporte@flowmatik.co
- **Documentación:** [docs.flowmatik.co](https://docs.flowmatik.co)
- **GitHub Issues:** [Reportar problema](https://github.com/tu-usuario/flowmatik-backend/issues)

## 📄 Licencia

MIT License - Ver archivo `LICENSE` para más detalles.

---

**Desarrollado con ❤️ por el equipo de Flowmatik**

*Potenciando la creación de contenido con IA de última generación*

