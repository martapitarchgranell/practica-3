#include <WiFi.h>         // Llibreria per gestionar la connexió WiFi a l'ESP32
#include <WebServer.h>    // Llibreria per crear un servidor web

// Credencials de la xarxa WiFi
const char* ssid = "*****";       // Nom de la xarxa WiFi (SSID)
const char* password = "*****";   // Contrasenya de la WiFi

// Creació d'un servidor web en el port 80 (port HTTP per defecte)
WebServer server(80);  

// --- CONFIGURACIÓ INICIAL ---
void setup() {
    Serial.begin(115200); // Iniciem la comunicació sèrie per debugar
    Serial.println("Try Connecting to ");
    Serial.println(ssid);

    // Intentem connectar-nos a la xarxa WiFi
    WiFi.begin(ssid, password);

    // Esperem fins que l'ESP32 es connecti a la xarxa
    while (WiFi.status() != WL_CONNECTED) { 
        delay(1000);
        Serial.print(".");  // Imprimeix punts per indicar que està connectant
    }

    Serial.println("");  
    Serial.println("WiFi connected successfully");  // Missatge de confirmació
    Serial.print("Got IP: ");
    Serial.println(WiFi.localIP());  // Mostra la IP assignada a l'ESP32

    // Assignem la funció `handle_root` per gestionar les peticions a la pàgina principal "/"
    server.on("/", handle_root);
    
    // Comencem el servidor web
    server.begin();
    Serial.println("HTTP server started");

    delay(100);
}

// --- BUCLE PRINCIPAL ---
void loop() {
    server.handleClient();  // Gestiona les peticions dels clients web
}

// --- CONTINGUT DE LA PÀGINA WEB (HTML) ---
String HTML = "<!DOCTYPE html>\
<html>\
<body>\
<h1>My Primera Pagina con ESP32 - Station Mode &#128522;</h1>\
</body>\
</html>";

// --- GESTIÓ DE LES PETICIONS WEB ---
// Aquesta funció s'executa quan un client accedeix a la IP de l'ESP32
void handle_root() {
    server.send(200, "text/html", HTML);  // Envia el contingut HTML al client
}
