# Project-Compose-Pantry

Docker Compose setup for running a lightweight Tailscale container alongside [Mealie](https://github.com/mealie-recipes/mealie), providing secure remote access and local availability.

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/jbledua/Project-Compose-Pantry.git
   cd Project-Compose-Pantry
    ```

2. **Configure environment variables**
   Copy the example file and update values as needed:

   ```bash
   cp .env.example .env
   ```

3. **Start the stack**

   ```bash
   docker compose up -d
   ```

---

## ⚙️ Services

* **Tailscale** – Secure networking and remote access.
* **Mealie** – Recipe manager, available:

  * **Locally**: http\://`<docker-host-ip>`:`PUBLIC_PORT`
  * **Remotely**: via Tailscale after running `tailscale serve`.

---

## ⚙️ Environment Variables

These values are defined in `.env.example` and should be customized in your `.env` file:

| Variable                          | Description                                                               |
| --------------------------------- | ------------------------------------------------------------------------- |
| **STACK\_NAME**                   | Name prefix for the Docker stack and containers.                          |
| **TS\_HOSTNAME**                  | Hostname to register this container with in Tailscale.                    |
| **TS\_AUTHKEY**                   | [Tailscale auth key](https://tailscale.com/kb/1085/auth-keys/) for login. |
| **PUBLIC\_PORT**                  | Local port on the Docker host to expose Mealie (e.g., 9925).              |
| **MEALIE\_BASE\_URL**             | Base URL for the Mealie application (used for links).                     |


---

## 📄 Files

* **`docker-compose.yml`** – Defines the services and configuration.
* **`.env.example`** – Example environment variables for customizing your deployment.

---

## 🔑 HTTPS Proxy Command (Optional)

Once deployed, you can expose Mealie (or any service) over Tailscale with:

```bash
sudo docker exec -it [Container Name] tailscale serve -bg 9000
```

This will make your service available over HTTPS via Tailscale.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE.md).
