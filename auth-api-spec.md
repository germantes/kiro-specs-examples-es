# SPEC: Endpoints de Autenticación (Login/Registro) en Node.js

## Contexto
Necesito crear los controladores para un sistema de autenticación básico usando Node.js, Express y JWT (JSON Web Tokens).

## Requisitos Técnicos
- **Framework:** Express.js.
- **Base de datos:** PostgreSQL (usando Prisma como ORM).
- **Librerías requeridas:** `bcryptjs` (para contraseñas), `jsonwebtoken` (para los tokens).

## Tareas a generar por Kiro
1. Escribir una función `registerUser` que reciba email y contraseña, hashee la contraseña con un "salt" de 10 rondas y guarde el usuario en la base de datos.
2. Escribir una función `loginUser` que verifique las credenciales y, si son correctas, devuelva un JWT válido por 24 horas.
3. Escribir un middleware `verifyToken` para proteger otras rutas de la API comprobando que el header `Authorization: Bearer <token>` sea válido.

## Restricciones y Casos Borde
- Si en el registro el email ya existe, debe devolver un error HTTP 409 (Conflict).
- No devuelvas nunca la contraseña hasheada en la respuesta JSON al cliente.
- Maneja los errores de base de datos con un bloque `try/catch` y devuelve un error HTTP 500 genérico si falla.
