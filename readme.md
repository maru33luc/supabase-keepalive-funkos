# Supabase Keep-Alive – FunkoStoreDB 🎯

Este proyecto utiliza **GitHub Actions** para mantener despierta la base de datos de **FunkoStore** en **Supabase Free Tier**.
Como Supabase en el plan gratuito entra en *sleep mode* cuando no recibe tráfico, este workflow envía automáticamente requests cada 5 minutos a la API REST del proyecto, evitando que la base se pause.

---

## 🚀 ¿Cómo funciona?

* GitHub Actions ejecuta un cron job cada **5 minutos**.
* Se envía una consulta `SELECT * FROM users LIMIT 1` a la API REST de Supabase.
* Esto es suficiente para mantener la base **Funkos DB** siempre arriba y lista para responder.

---

## ⚙️ Configuración

1. **Fork o cloná este repo** en tu cuenta de GitHub.
2. En GitHub, andá a:
   `Settings → Secrets and variables → Actions → New repository secret`.

   * **Name:** `SUPABASE_ANON_KEY`
   * **Value:** tu `anon public key` de Supabase (*Project Settings → API*).
3. Revisá el archivo `.github/workflows/keepalive.yml` y asegurate de que la URL sea la de tu proyecto:

   ```
   https://dmnqaexxghiuzjgtrtj.supabase.co
   ```
4. Ajustá la tabla si querés (por defecto usa `users`):

   ```yaml
   curl -s "https://<PROJECT>.supabase.co/rest/v1/users?limit=1"
   ```

---

## 📂 Estructura del proyecto

```
.
├── .github
│   └── workflows
│       └── keepalive.yml   # Workflow de GitHub Actions
└── README.md
```

---

## 🛠️ Uso

* El workflow corre automáticamente **cada 5 minutos**.
* También podés ejecutarlo manualmente desde la pestaña **Actions** en GitHub.

---

## 📦 Tecnologías utilizadas

* [Supabase](https://supabase.com/) – Base de datos PostgreSQL + API REST.
* [GitHub Actions](https://docs.github.com/en/actions) – Automatización y cron jobs.
* [cURL](https://curl.se/) – Requests HTTP ligeros.

---

## 🎉 Resultado

Con este setup, tu **FunkoStoreDB** estará siempre lista para manejar consultas, sin entrar en sleep mode aunque uses el **plan gratuito** de Supabase.
