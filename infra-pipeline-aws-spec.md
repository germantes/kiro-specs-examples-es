# SPEC: Pipeline CI/CD para despliegue en AWS ECS

## Contexto
Necesitamos crear un flujo de trabajo (workflow) en GitHub Actions para automatizar el testing, la construcción de una imagen Docker y su despliegue en Amazon Elastic Container Service (AWS ECS) utilizando AWS Fargate.

## Requisitos Técnicos
- **Herramienta CI/CD:** GitHub Actions.
- **Destino:** AWS ECR (Elastic Container Registry) y AWS ECS (Fargate).
- **Triggers:** El pipeline solo debe ejecutarse cuando se haga un `push` a la rama `main`.

## Tareas a generar por Kiro
1. Escribir el archivo `.github/workflows/deploy.yml`.
2. Configurar el paso de autenticación con AWS utilizando `aws-actions/configure-aws-credentials` (usando OIDC, no claves a largo plazo).
3. Añadir el paso de login a Amazon ECR.
4. Construir, etiquetar (con el SHA del commit) y subir (push) la imagen Docker a ECR.
5. Actualizar la definición de la tarea (Task Definition) de ECS y desplegar el servicio.

## Criterios de Aceptación y Seguridad
- El código generado no debe contener credenciales hardcodeadas (usa `secrets.AWS_ROLE_ARN`).
- Debe incluir un paso previo (Job) para correr tests (`npm test`) antes de construir la imagen. Si los tests fallan, el despliegue se cancela.
- El archivo YAML debe estar bien indentado y comentado en español para que el equipo lo entienda.
