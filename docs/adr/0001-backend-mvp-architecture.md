# ADR 0001 — Arquitectura MVP Backend

## Estado
Aceptado

## Contexto
Se requiere definir la arquitectura del backend del MVP para el alta y perfil
de prestadores de servicios, priorizando escalabilidad, bajo acoplamiento y
facilidad de evolución futura.

El sistema deberá soportar validación por WhatsApp, gestión de perfiles,
categorías múltiples y futuras integraciones (pagos, chat, RENAPER).

## Decisión
Adoptar una arquitectura backend basada en:

- Node.js 20 LTS
- NestJS como framework principal
- PostgreSQL como base de datos relacional
- Prisma como ORM y gestor de migraciones
- Autenticación mediante JWT
- Validación de teléfono por WhatsApp (OTP) mediante abstracción de proveedor

La arquitectura será modular, organizada por dominios funcionales
(vertical slices).

## Estructura de módulos
- auth
- providers
- categories
- whatsapp
- database
- common

## Convenciones
- Prefijo global de API: `/api/v1`
- DTOs para validación
- Estados explícitos del perfil (BORRADOR, ACTIVO, SUSPENDIDO)
- No acoplar lógica de negocio a proveedores externos

## Alternativas consideradas
- Express sin framework (descartado)
- Firebase (descartado por lock-in)
- TypeORM (descartado en favor de Prisma)

## Consecuencias
### Positivas
- Escalabilidad clara
- Base sólida para crecimiento
- Testing y mantenimiento facilitados

### Negativas
- Mayor estructura inicial
- Curva de aprendizaje de NestJS

## Estado futuro
Este ADR podrá ampliarse cuando se incorporen:
- Pagos escrow
- Chat interno
- Geolocalización avanzada
