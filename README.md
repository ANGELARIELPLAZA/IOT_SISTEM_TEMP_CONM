```markdown
# 🔧 Sistema de Monitoreo y Control Automatizado de Temperatura para Salas de Conmutación (IoT)

Este proyecto implementa un sistema IoT para la **medición, visualización y control automático** de temperatura y humedad en salas de conmutación, con el objetivo de garantizar la continuidad operativa de los equipos de telecomunicaciones.

## 📦 Tecnologías Utilizadas

- **Docker & Docker Compose**
- **Mosquitto (MQTT Broker)**
- **Node-RED (automatización y lógica de control)**
- **MongoDB (almacenamiento de datos)**
- **Prometheus + Grafana (monitorización y dashboards)**
- **ESP32 + Sensores DHT22** (hardware externo, opcional)

---

## 📁 Estructura del Proyecto

```
📦 proyecto-iot-sala
 ┣ 📂 mosquitto
 ┃ ┗ 📄 mosquitto.conf
 ┣ 📂 prometheus
 ┃ ┗ 📄 prometheus.yml
 ┣ 📂 node-red-data
 ┣ 📄 .env
 ┣ 📄 docker-compose.yml
 ┗ 📄 README.md
```

---

## ⚙️ Variables de entorno (`.env`)

```env
MONGO_USER=root
MONGO_PASS=ejemplo123

GRAFANA_USER=admin
GRAFANA_PASS=admin123
```

---

## 🚀 Cómo iniciar el sistema

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/proyecto-iot-sala.git
   cd proyecto-iot-sala
   ```

2. Crea el archivo `.env` con las credenciales necesarias.

3. Levanta los servicios:
   ```bash
   docker-compose --env-file .env up -d
   ```

4. Accede a las interfaces:
   - Node-RED: [http://localhost:1880](http://localhost:1880)
   - Grafana: [http://localhost:3000](http://localhost:3000)
   - Prometheus: [http://localhost:9090](http://localhost:9090)

---

## 🔌 Flujo General del Sistema

1. **Sensores IoT** (DHT22) miden temperatura y humedad.
2. **ESP32** publica los datos por **MQTT** hacia **Mosquitto**.
3. **Node-RED** procesa los datos, los guarda en **MongoDB** y activa ventiladores/A/C según lógica.
4. **Prometheus** recolecta métricas y **Grafana** las visualiza en tiempo real.
5. Se envían alertas si los valores están fuera de rango.

---

## 📊 Dashboards y Visualización

Una vez configurado Grafana, puedes crear dashboards personalizados o importar paneles desde el repositorio oficial.

---

## 🔐 Seguridad

- El acceso a Grafana y MongoDB se encuentra protegido por credenciales definidas en el archivo `.env`.
- MQTT está habilitado como **público temporalmente** para pruebas (modificable en `mosquitto.conf`).

---

## ✍️ Autor

**Angel Ariel Plaza**  
Proyecto para el Instituto Tecnológico Superior de Coatzacoalcos  
Periodo: Enero - Junio 2025  

---

## 📄 Licencia

Este proyecto se distribuye bajo la Licencia MIT.
