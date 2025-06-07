#include <WiFi.h>
#include <WebServer.h>

// 🔹 Configuració del Punt d'Accés
const char* ssid = "ESP32-AP";      // Nom de la xarxa WiFi (SSID)
const char* password = "12345678";  // Contrasenya (mínim 8 caràcters)

WebServer server(80);  // Crear servidor HTTP al port 80

// 🌐 Pàgina web HTML bàsica
String HTML = "<!DOCTYPE html>\
<html>\
<body>\
<h1>ESP32 Access Point Mode</h1>\
<p>Dispositiu ESP32 funcionant com a Punt d'Accés.</p>\
</body>\
</html>";

// 📌 Funció que s'executa quan accedim a la pàgina web
void handle_root() {
    server.send(200, "text/html", HTML);
}

void setup() {
    Serial.begin(115200);
    Serial.println("Configurant Punt d'Accés...");

    // 🛜 Creació del Punt d'Accés
    WiFi.softAP(ssid, password);

    // 🔹 Obtenir i mostrar la IP del AP
    IPAddress IP = WiFi.softAPIP();
    Serial.print("AP IP address: ");
    Serial.println(IP);

    // 🌐 Configuració del servidor web
    server.on("/", handle_root);
    server.begin();
    Serial.println("Servidor web iniciat!");
}

void loop() {
    server.handleClient();  // Gestiona les peticions HTTP
}
