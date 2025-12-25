# Prompt Engineering Library para Claude Code
## Sistema de Prompts Multi-Agente con Testing y Verificación

**Creado:** 2025-12-25
**Propósito:** Librería modular de prompts especializados para desarrollo profesional con Claude Code

---

## 📁 Estructura del Proyecto

```
prompt-engineering/
├── README.md                          # Este archivo
├── core/
│   ├── base-programming.md            # Prompt base para programación
│   ├── error-prevention.md            # Prevención de errores (anti-suposiciones)
│   └── multi-agent-orchestration.md   # Orquestación de agentes
├── agents/
│   ├── backend-developer.md           # Agente especializado backend
│   ├── frontend-developer.md          # Agente especializado frontend
│   ├── testing-engineer.md            # Agente de testing y QA
│   ├── devops-engineer.md             # Agente DevOps/deployment
│   ├── data-analyst.md                # Agente análisis de datos
│   └── ui-ux-specialist.md            # Agente UI/UX
├── workflows/
│   ├── tdd-workflow.md                # Test-Driven Development
│   ├── parallel-development.md        # Desarrollo paralelo multi-agente
│   └── verification-protocol.md       # Protocolo de verificación y evidencia
├── templates/
│   ├── task-decomposition.md          # Template descomposición de tareas
│   ├── evidence-report.md             # Template reporte de evidencia
│   └── agent-handoff.md               # Template handoff entre agentes
└── examples/
    ├── case-study-vox-client.md       # Caso de estudio: VOX Client
    └── best-practices-learned.md      # Lecciones aprendidas
```

---

## 🎯 Objetivos

1. **Eliminar suposiciones**: Verificar antes de ejecutar
2. **Testing planificado**: TDD y verificación continua
3. **Multi-agente eficiente**: Paralelización de tareas especializadas
4. **Evidencia documental**: Cada cambio con prueba de funcionamiento
5. **Reproducibilidad**: Workflows repetibles y auditables

---

## 🚀 Inicio Rápido

### Para usar un agente específico:

```bash
# En Claude Code:
/task "Usa el agente backend-developer para implementar API REST"
```

### Para workflow multi-agente:

```bash
# En Claude Code:
/task "Usa parallel-development workflow:
  - Agente 1 (backend): API endpoints
  - Agente 2 (frontend): UI components
  - Agente 3 (testing): Unit tests
  Ejecutar en paralelo"
```

---

## 📚 Principios Fundamentales

### 1. **NO SUPONER - VERIFICAR**
- ✅ Ejecutar `ls`, `file`, `grep` antes de asumir
- ✅ Leer código existente antes de modificar
- ✅ Verificar encoding y line endings
- ❌ Nunca asumir rutas de archivos
- ❌ Nunca asumir estructura sin verificar

### 2. **TESTING FIRST**
- ✅ Escribir tests antes de implementar (TDD)
- ✅ Verificar con ejecución real (no solo linting)
- ✅ Documentar resultados de tests
- ❌ Nunca marcar completado sin evidencia
- ❌ Nunca "asumir que funciona"

### 3. **MULTI-AGENTE ESPECIALIZADO**
- ✅ Un agente = una responsabilidad clara
- ✅ Ejecución paralela cuando sea posible
- ✅ Handoffs documentados entre agentes
- ❌ Nunca mezclar responsabilidades
- ❌ Nunca ejecutar secuencialmente si puede ser paralelo

### 4. **EVIDENCIA OBLIGATORIA**
- ✅ Capturar output de comandos
- ✅ Screenshots de UI cuando aplique
- ✅ Logs de tests pasando
- ✅ Diff de cambios relevantes
- ❌ Nunca reportar sin prueba

---

## 🔧 Configuración Inicial

### Instalar comandos en tu proyecto:

```bash
# Copiar templates a tu proyecto
cp -r prompt-engineering/.claude/commands /tu-proyecto/.claude/

# Hacer disponibles los agentes
git add .claude/
git commit -m "Add prompt engineering agents"
```

### Estructura recomendada en tu proyecto:

```
tu-proyecto/
├── .claude/
│   ├── commands/
│   │   ├── backend.md      # /backend
│   │   ├── frontend.md     # /frontend
│   │   ├── test.md         # /test
│   │   └── verify.md       # /verify
│   └── CLAUDE.md           # Configuración del proyecto
```

---

## 📖 Guías de Uso

### Caso 1: Desarrollo de Feature Completa

```markdown
Prompt inicial:
"Implementar sistema de autenticación JWT usando multi-agente workflow:

Agente 1 (backend-developer):
- Crear endpoints /login, /register, /verify
- Usar bcrypt para passwords
- Generar JWT tokens
- Tests unitarios con pytest

Agente 2 (frontend-developer):
- Formularios login/register en React
- Manejo de tokens en localStorage
- Protected routes
- Tests con React Testing Library

Agente 3 (testing-engineer):
- Tests de integración E2E
- Casos de error (401, 403, 500)
- Performance tests
- Security audit

Ejecutar agentes en paralelo. Reportar evidencia de cada agente."
```

### Caso 2: Debugging con Evidencia

```markdown
"Usar verification-protocol para debug:

1. Reproducir el error (capturar stacktrace)
2. Identificar root cause (no suponer)
3. Proponer fix con test que falla
4. Implementar fix
5. Verificar test pasa
6. Reportar evidencia completa"
```

---

## 🎓 Mejores Prácticas Aprendidas

### De la experiencia VOX Client v2.0.21:

#### ❌ **Errores cometidos:**
1. Crear múltiples versiones (a, b, c, d, e, f, g) sin verificar
2. Asumir encoding UTF-8 funciona en PowerShell Windows
3. Asumir rutas relativas sin verificar estructura
4. No probar sintaxis antes de empaquetar
5. No documentar cambios entre versiones

#### ✅ **Soluciones aplicadas:**
1. **Verificación pre-empaquetado:** `file`, `grep`, estructura manual
2. **Testing de encoding:** Convertir a ASCII + CRLF para Windows
3. **Verificación de rutas:** `Test-Path` con fallback
4. **Versionado semántico:** Letra = tipo de cambio (a=docs, b=permisos, c=syntax, etc.)
5. **CHANGELOG.txt:** Documentar cada cambio

---

## 📊 Métricas de Éxito

### KPIs para evaluar efectividad:

- **Tasa de éxito primer intento:** >80% (vs ~30% sin prompts)
- **Versiones desperdiciadas:** <3 por feature
- **Tests automáticos:** 100% de features con tests
- **Tiempo de debugging:** <20% del tiempo total
- **Evidencia documental:** 100% de tasks completadas

---

## 🔄 Roadmap

### Fase 1: Core Library (Actual)
- [x] Estructura base del proyecto
- [ ] Prompts core fundamentales
- [ ] 6 agentes especializados
- [ ] 3 workflows principales

### Fase 2: Templates & Examples
- [ ] Templates reutilizables
- [ ] Casos de estudio documentados
- [ ] Biblioteca de snippets comunes

### Fase 3: Automatización
- [ ] Scripts de deployment de prompts
- [ ] CI/CD para validación de prompts
- [ ] Dashboard de métricas

---

## 🤝 Contribución

Para agregar nuevos prompts:

1. Crear archivo en directorio correspondiente
2. Seguir estructura de template
3. Incluir ejemplos de uso
4. Documentar casos de éxito/fallo
5. Agregar a este README

---

## 📝 Licencia

Libre uso interno. Compartir mejoras con el equipo.

---

**Última actualización:** 2025-12-25
**Mantenedor:** API Production Team
**Contacto:** mc@itecnis.com
