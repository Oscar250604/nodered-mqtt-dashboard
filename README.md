# Node-RED + MQTT Dashboard

Dashboard de monitoreo de temperatura con Node-RED, Mosquitto (MQTT) y Docker.

## Componentes
- **Mosquitto**: broker MQTT (puerto 1883, WebSockets 9001)
- **Node-RED**: flujos y dashboard (puerto 1880)
- **Dashboard 2.0** (`@flowfuse/node-red-dashboard`): gauge y gráfica de historial

## Flujo
1. Un nodo `inject` genera cada 2 s una temperatura simulada (20–35 °C).
2. Se publica por MQTT en el tema `sensores/temperatura`.
3. Un nodo `mqtt in` suscrito a `sensores/#` la envía al gauge y a la gráfica.

## Cómo ejecutar
```bash
docker compose up -d
```
- Node-RED: http://localhost:1880
- Dashboard: http://localhost:1880/dashboard/page1

## Importar los flujos
En Node-RED: menú ☰ → Importar → selecciona `flows.json`.
Instala antes `@flowfuse/node-red-dashboard` desde Gestionar paleta.
