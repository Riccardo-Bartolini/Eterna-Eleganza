# Eterna Eleganza

**A watch e-commerce application built with PHP, MySQL and Twig.**

![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4?style=flat&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Twig](https://img.shields.io/badge/Templates-Twig-6E963B?style=flat)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

Developed by **Riccardo Bartolini and Gianmaria Di Fronzo** for the **Web Technologies** course at the **University of Bologna**, academic year 2024/2025.

The project connects a customer-facing catalogue and checkout flow with vendor tools for managing products and orders. It combines server-rendered pages, JavaScript interactions and a relational database.

## Features

- Product catalogue, filters and individual product pages.
- Customer registration, login and a private account area.
- Shopping cart and checkout workflow.
- Vendor product creation and management, with order views.
- User notifications and order information.

The checkout is part of an academic demonstration; this repository does not document an integration with a payment provider.

## Architecture and data model

The PHP application separates request controllers, database models and Twig-backed views. JavaScript provides cart and checkout interactions in the browser.

The database schema defines users, notifications, products, orders and order contents. It uses primary keys, foreign keys and a composite key for the order-content relationship, with referential actions for related records.

| Path | Purpose |
| :--- | :--- |
| [`Ecommerce/index.php`](Ecommerce/index.php) | Application entry point and request dispatcher. |
| [`Ecommerce/controller/`](Ecommerce/controller/) | Customer and vendor request handling. |
| [`Ecommerce/models/`](Ecommerce/models/) | Database access and domain data. |
| [`Ecommerce/views/`](Ecommerce/views/) | View rendering. |
| [`Ecommerce/templates/`](Ecommerce/templates/) | Twig pages and application assets. |
| [`Ecommerce/config/table_creation.SQL`](Ecommerce/config/table_creation.SQL) | Database schema and synthetic demonstration data. |
| [`frontend/`](frontend/) | Standalone interface prototypes and assets. |
| [`Mockup/`](Mockup/) | Original interface mockups. |
| [`report.pdf`](report.pdf) | Project report. |
| [`DiagrammaWorkflow.pdf`](DiagrammaWorkflow.pdf) | Workflow diagram. |

## Local setup

This repository preserves the university submission. Setup requires manual database and web-server configuration; a reproducible end-to-end installation has not yet been verified.

### Requirements

- **PHP 8.2 or later**, required by the locked Symfony Asset dependency.
- **Composer**.
- **MySQL**, PHP `pdo_mysql` and `mysqli` extensions.
- A local PHP-capable web server configured to route application URLs to `Ecommerce/index.php` and serve the files under `Ecommerce/templates/public/`.

### Preparation

```bash
git clone https://github.com/Riccardo-Bartolini/web-application-project.git
cd web-application-project/Ecommerce
composer install
```

Install dependencies from `Ecommerce/`, which contains the application's own `composer.json` and lockfile. The separate manifest at the repository root is not the complete application manifest.

1. Create a local MySQL database and import [`config/table_creation.SQL`](Ecommerce/config/table_creation.SQL). Use an empty demo database; the script creates tables and inserts sample records.
2. Configure [`config/config.php`](Ecommerce/config/config.php) for that local database. Keep actual credentials private and do not commit local values.
3. Configure the web server with `Ecommerce/` as the application directory and front-controller routing for paths such as `/login` and `/catalogo_prodotti`.
4. Verify catalogue loading, registration/login, cart/checkout and vendor views locally.

The SQL file contains synthetic demonstration records. The application and its configuration should be reviewed before any deployment beyond local development.

## Validation and current scope

The source, dependency manifests, schema and report are included. A complete automated test suite and verified deployment configuration are not currently provided. The next improvements are environment-based database configuration, repeatable setup and regression tests for customer and vendor workflows.

## Credits and licensing

This is a team project by **Riccardo Bartolini and Gianmaria Di Fronzo**. The report documents the submitted design and implementation; the repository does not yet distinguish each author's individual tasks.

A project-wide license has not yet been added. The authors need to agree on the license for their shared code before one is published. Bundled dependencies retain their own licenses, including the notices under `Ecommerce/vendor/`; those notices do not automatically license the application itself.
