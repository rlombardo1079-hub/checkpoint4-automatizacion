# Pre-entrega 4: Sincronización del Cerebro Agéntico con Ecosistemas de Negocio

## 📋 Descripción del Proyecto
Este repositorio contiene la evolución del proyecto integrador (Módulo 4), donde se conectó e interconectó de forma bidireccional el agente autónomo con tres herramientas del negocio bajo protocolos seguros OAuth2 y estrictas políticas de menor privilegio:
1. **CRM (HubSpot):** Gestión centralizada de contactos con lógica de upsert para evitar duplicados.
2. **Casilla de Correo (Gmail):** Automatización de recepción con filtros de seguridad y creación de borradores.
3. **Canal del Equipo (Slack):** Notificaciones operativas en tiempo real para el equipo de operaciones.

---

## 🔐 Evidencia de Conectividad (Credentials)
*Captura de la sección **Credentials** en n8n validando el estado de autenticación OAuth2 de las 3 herramientas:*

![Credenciales de n8n](./credenciales.png)

---

## 🛠️ Arquitectura y Guardrails implementados
El flujo incorpora las barreras de seguridad y optimizaciones requeridas:
- **Filtro Anti Auto-reply:** Control IF inicial para neutralizar bucles de respuestas automáticas y correos genéricos (`no-reply@`).
- **Prevención de Conflictos (Error 409):** Uso de la operación inteligente de HubSpot para la búsqueda y actualización de contactos sin duplicados.
- **Human-in-the-loop (HITL):** Configuración del nodo Gmail en modo `Create Draft` para asegurar que ningún mensaje se envíe de forma automatizada sin revisión previa.
- **Limpieza de Payload:** Normalización de datos para evitar cargas pesadas o desbordes en los canales de notificación.

---

## 📂 Archivo del Workflow
- [`checkpoint4_Romina_Lombardo.json.json`](./checkpoint4_Romina_Lombardo.json.json): Archivo exportado listo para importar de forma directa en n8n.
