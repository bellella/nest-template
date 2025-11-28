## PROJECT TECHNICAL SPECIFICATION

### CORE STACK (Specs)

- Framework: **NestJS v10.x**
- ORM: **Prisma v7.x**
- Database: **PostgreSQL**
- API Documentation: **Swagger**
- Code Formatting: **Prettier**

### Environment Variables

```
DATABASE_URL=
JWT_SECRET=
ORIGIN_URL=
# file upload
S3_BUCKET=
S3_REGION=
S3_ACCESS_KEY=
S3_SECRET_KEY=
# mails
MAIL_HOST=
MAIL_USER=
MAIL_PASSWORD=
MAIL_FROM=
```

To run the project, create a **.env** file and define these required keys:

### MODULE FEATURES

- **auth**: ID/Password-based Login & Register, Google/Apple social Login & Register. Authentication tokens (JWTs) are managed exclusively via **HTTP-Only Cookies**. (Note: If session management is changed to exclude token generation, "JWT" must be removed from the description.)
- **file**: 3MB image cloud (S3 etc.) upload.
- **user**: User information Create, Read, Update, Delete (CRUD).
- **health**: Application status check endpoint.
- **mail**: Transaction-based email sending functionality.
- **prisma**: Prisma Client connection and DB adapter management.

### METHOD NAMING CONVENTION

Method names use **lowerCamelCase** and follow the **Verb (Action) + Object** structure, ensuring clarity and consistency across layers.

| Function             | Service/Repository (Data Access) | Controller (API Endpoint) | Rationale                                                                    |
| :------------------- | :------------------------------- | :------------------------ | :--------------------------------------------------------------------------- |
| **Single Retrieval** | `find...` (e.g., `findOneById`)  | `findOne`                 | Aligns with ORM standards (Prisma/TypeORM) for data access.                  |
| **List Retrieval**   | `find...` (e.g., `findAllUsers`) | `findAll`                 | Aligns with RESTful standards and NestJS/Express conventions.                |
| **Deletion**         | `delete...` (e.g., `deleteUser`) | `remove`                  | Separates DB standard (`delete`) from NestJS Controller standard (`remove`). |
| **Compound Action**  | `get...` (e.g., `getTokens`)     | `login` / `refresh`       | `get` is reserved for high-level functions involving business logic.         |
