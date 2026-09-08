# GCX — Gestor de cotizaciones
Sistema de gestión de cotizaciones y control de costos para el Área de Costos de Clínica MediCosta, Sincelejo.

## Stack
 
Laravel, Tailwind, SQLite, dompdf, Pest.

## Instalación local
 
    git clone <repositorio>
    cd gcx-cotizaciones
    composer install
    npm install
    cp .env.example .env
    php artisan key:generate
    touch database/database.sqlite
    php artisan migrate --seed
    npm run dev
    php artisan serve

## Decisiones de diseño que conviene conocer antes de tocar el código
 
**El sistema no mantiene catálogo de CUPS ni de UVR.** El usuario digita ambos como dato. Mantener
miles de códigos actualizados es un costo permanente que no resuelve el problema del Área.
 
**El motor tarifario es PHP puro, sin Eloquent.** Se puede probar y extender sin levantar la aplicación.
 
**Todo valor calculado se conserva junto al valor final.** Cuando el auxiliar sobrescribe un
cálculo, el sistema guarda ambos. Es el soporte ante una glosa por diferencia tarifaria.
 
**Cada cotización guarda la instantánea de su liquidación y la versión del tarifario usada.** Una
cotización de 2026 se reproduce igual aunque las tablas cambien después.
