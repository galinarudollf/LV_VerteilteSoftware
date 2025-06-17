# Kommunikationsprotokolle
## Schichtenmodell

- Komplexen Kommunikationsvorgänge werden in einzelne Schritte aufgegliedert und in mehreren Schichten übereinandergestapelt. 
- Jede Schicht definiert bestimmte Aufgaben und Funktionen. Zur Lösung dieser Aufgaben existieren spezielle Verfahren und Protokolle. 
- Jede Schicht verfügt jeweils über Schnittstellen zur darüber oder darunter liegenden Schicht.
- Die darunter liegenden Schichten sind „Übersetzer“ für darüber liegenden.
- Übertragungsweg, Protokolle und Anwendung genormt und genau spezifiziert.
- Referenzmodelle: OSI (Open System Interconnection model) und TCP/IP-Referenzmodell (DoD - Department of Defense)
    - OSI- Referenzmodell: theoretisches Konzept, Schichten unterstreicht verschiedene Aspekte der Kommunikation
    - TCP/IP-Referenzmodell: eine praktische Implementierung
- Für das Internet und die Internetprotokollfamilie wird die Gliederung nach TCP/IP-Referenzmodell verwendet.

Die Teile einer verteilten Anwendung, ob sie auf verschiedenen Rechner oder in verschiedenen Prozessen laufen, müssen miteinander kommunizieren. Threads können gemeinsame Daten zum Interagieren benutzen. Anders ist es wenn die Teile einer Anwendung in verschiedenen Prozessen (auf verschiedenen Rechner) laufen.
In der Computer- und Netzwerktechnik werden die komplexen Kommunikationsvorgänge in einzelne Schritte aufgegliedert und in mehreren Schichten übereinandergestapelt. Jede Schicht definiert für die Kommunikation zwischen zwei Systemen bestimmte Aufgaben und Funktionen. Zur Lösung dieser Aufgaben existieren in jeder Schicht spezielle Verfahren und Protokolle. Die untergeordneten Schichten stellen dabei den übergeordneten eine bestimmte Dienstleistung zur Verfügung. Jede Schicht verfügt jeweils über Schnittstellen zur darüber- oder darunterliegenden Schicht.
Das Schichtenmodell wird häufig mit der Kommunikation zwei Personen, die zwei unterschiedliche Sprachen sprechen, verglichen. Beide Personen sind wegen der unterschiedlichen Sprache nicht in der Lage direkt miteinander zu kommunizieren und bedienen sich deshalb eines (in geschlossenen proprietären Systemen) oder zwei (in offenen Systemen) Übersetzers.
In offenen Systemen sind Übertragungsweg, Protokolle und Anwendung genormt und genau spezifiziert.
Bekannt sind zwei Schichtenmodelle. Das OSI-Schichtenmodell und das DoD-Schichtenmodell (auch TCP/IP-Referenzmodell genannt). Obwohl das Internet und damit alle Netzwerke auf dem DoD-Schichtenmodell basieren, wird vielfach auf das OSI-Schichtenmodell Bezug genommen. Das OSI-Schichtenmodell wurde später entwickelt, ist feiner gegliedert und flexibler. So lässt das OSI-Schichtenmodell die Zusammenfassung oder Entfernung einzelner Schichten zu.

![Schichtmodell](images/sockets/schichtmodell.png)

Quelle: https://de.wikipedia.org/wiki/Internetprotokollfamilie#TCP/IP-Referenzmodell

## Schichten des TCP/IP Referenzmodells für Netzprotokolle

- Netzzugang (Link Layer)
Techniken (mechanische und elektrische Mittel) der Datenübertragung von Punkt zu Punkt
   - Physical Layer: Bitübertragungsschicht
   - Sicherungschicht (Data Link Layer): Aufteilen des Bitstroms in Blöcke (Frames), Hinzufügen von Prüfsummen etc. 

Die Netzzugangsschicht ist im Modell zwar spezifiziert, enthält aber keine Protokolle der TCP/IP-Familie. Sie ist vielmehr ein Platzhalter für verschiedene Techniken der von Punkt zu Punkt Datenübertragung und entspricht der Sicherungs- und Bitübertragungsschicht des OSI-Referenzmodells.

- Internet (Internet Layer)
Vermittlung von Datenpaketen über den gesamten Kommunikationsweg:
    - Routing (Wegsuche) zwischen den Netzknoten 
    - eindeutige Adressierung durch IP (Internet Protocol)

Die Internetschicht ist für die Vermittlung von Paketen und die Wegsuche zuständig. Die Aufgabe dieser Schicht ist es, zu einem empfangenen Paket das nächste Zwischenziel zu ermitteln und das Paket dorthin weiterzuleiten. Der Kern dieser Schicht ist das Internet Protocol (IP) mit dem eine eindeutige Adressierung ermöglicht wird. Die Internetschicht entspricht der Vermittlungsschicht des OSI-Referenzmodells.

- Transport (Transport Layer) 
Ende-zu-Ende-Kommunikation Adressierung wird durch „Kontaktpunkte“ (Portnummern) ergänzt
    - Transportprotokolle 
        - UDP (User Datagram Protocol)
        - TCP (Transmission Control Protocol)

Die Transportschicht ermöglicht eine Ende-zu-Ende-Kommunikation. Die IP-Adressierung wird durch „Kontaktpunkte“ (Portnummern) ergänzt. Das wichtigste Protokoll dieser Schicht ist das Transmission Control Protocol (TCP), das die sichere Verbindungen zwischen jeweils zwei Netzwerkteilnehmern ermöglicht. Es gehört aber auch das unzuverlässige User Datagram Protocol (UDP) in diese Schicht.

- Anwendung (Application Layer)
stellt alle Protokolle für die Anwendungen zur Verfügung, ist zuständig für Verbindung zu den unteren Schichten
    - Session  Layer: Protokolle zum organisierten und synchronisierten Datenaustausch wie RPC (Remote Procedure Call)
    - Presentation Layer: Umwandlung systemabhängiger Daten, Anpassung zw. Systemen, Datenkompression und Verschlüsselung

## Internet – Adressen 
jede IP-Adresse ist weltweit eindeutig

Damit Nachrichten, Pakete bzw. generell Kommunikationsanfragen das richtige Adressat finden, wird jedem Verbindungspunkt (jedem Rechner in Internet) eine eindeutige und zwar eine weltweit eideutige IP-Adresse zugeordnet. Internet Protocol gibt es in den Versionen 4 und 6. 
Mit IPv4 ist die Adressierung von theoretisch vier Milliarden Rechner möglich. Da aber mit der Zeit das Internet immer größere Verbreitung erlangte, war zu befürchten, dass die Adressen nicht ausreichen werden. Im Dezember 1998 wurde IPv6 offiziell zum Nachfolger von IPv4 ernannt. Damit wurde die Vergrösserung des Adressraums auf 340 Sextllionen erreicht.

**IPv4:**

32 Bit, 4X8, (2 hoch 32 Adressen)

Dezimalnotation 
0..255,  d.d.d.d	139.20.17.101

```  
<244 	   einzelne Rechner (Unicast) – Adressen-Klassen A, B und C
224.. 239  D-Klasse: Multicast-Adressen, Gruppen-Adressen von 224.0.0.0 bis 239.255.255.255 (jede mit FF00::/8 beginnende Adr.)
>239 	   E-Klasse: reservierter Bereich
```

**IPv6:** (seit 1998)

128 Bit, 8X16, (2 hoch 128 Adressen)		
Hexadezimalnotation, (0..ffff)  
2001:0db8:0000:0000:0000:ff00:0042:8329

Namen (z.B. www.informatik.tu-freiberg.de) werden in IP-Adresse vom Domain Name System (DNS) umgesetzt

Die IP-Adressen, speziell IPv6 stellen für Rechner kein Problem dar, für uns Menschen mit den Namen zu agieren ist dennnoch viel angenehmer als mit den Nummern. Es werden deswegen parallel zu den Adressen hierarchisch aufgebaute Namen geführt, z.B. www.informatik.tu-freiberg.de
Die Namen werden von Domain Name System (DNS) in IP-Adresse umgesetzt. Der eigentliche Name des Rechners wird auch als Host-Name (oder einfach Host) bezeichnet.

## Kommunikationsformen

### Unicast
Übertragung von Nachrichten zwischen einem Sender 
und einem einzigen Empfänger - genau ein Ziel

**Spezielle Adressen:**
unspezifiziert 	  	0.0.0.0	 [::]
loopback (localhost)	127.0.0.1	 [::1]

### Multicast
eine Nachrichtenübertragung von einem Punkt zu einer Gruppe - mehrere Ziele

![Multicast](images/sockets/multicast.png)

### Broadcast
eine spezielle Form der Mehrpunktverbindung (alle Teilnehmer eines lokalen Netzwerks)
 	eigenes lokales Netz: 255.255.255.255

![broadcast](images/sockets/broadcast.png)

## Klasse  InetAddress 

- geeignet für beide IP-Adresstypen, 
- Spezielle Klassen: Inet4Address, Inet6Address

Anlegen des Objektes:

```java
static InetAddress getLocalHost() throws UnknownHostException
static InetAddress getByName(String host) throws UnknownHostException
static InetAddress getByAddress(byte[] addr) throws UnknownHostException

InetAddress ia1 = InetAddress.getByName("pc1.informatik.tu-freiberg.de");
InetAddress ia2 = InetAddress.getLocalHost();
```

Weitere Methoden:
```java
String getHostname()		//Rechnername
String getCanonicalHostName()	//qualifizierter Domainame
String getHostAddress()		//IP-Adresse
byte[] getAddress()		//IP-Adresse
```

Achtung: Die Adresse allein reicht nicht zur Identifizierung einer Internet-Ressource (einer Webseite, Webservice, Email-Empfänger, Datei, …)!
Eindeutige Identifikation benötigt mehr Informationen, z.B. Art der Ressource ….

## Uniform Resource Identifier (URI)

```
scheme ":" [ authority ] path [ "?" query ] [ "#" fragment ] 
```

- Schema oder Protokoll (Art der Ressource)	
	z.B. https, ftp, mailto, tel, …
- Anbieter oder Server (authority) inkl.  Host (Name, IPv4, IPv6), Portnummer (Integer-Wert) 
- Pfad		
- Abfrage – Query-String mit zusätzlichen Informationen (evtl.)
- Fragment (evtl.)

Beispiele:
```
https://beispiel.de:8042/pfad/nochpfad?abfrage=text#stelle
https://de.wikipedia.org/wiki/Uniform_Resource_Identifier  
tel:+49-111-111-111
mailto:anonymous@info.com
telnet://179.20.17.102
geo:50.91,13.34;u=400

```
- Bei URI geht es nur darum, die Resource zu identifizieren, nicht um den Zugriffsmechanismus!
- Uniform Resource Locator (URL) identifiziert und lokalisiert eine Ressource u.a. über die Zugriffsmethode (Protokoll), erste und häufigste Art von URI
- Uniform Resource Name URN (weltweit eindeutiger Name), z.B. urn:ISBN:3-8273-7019-1 

### Klasse URI

```java
//hat mehrere Konstruktoren
public URI(String scheme,		
           String userInfo,	
           String host,		
           int port,			
           String path,		
           String query,		
           String fragment) throws URISyntaxException
```

## Uniform Resource Locator (URL) 

### Klasse URL 

```java
//bis Java 20: mehrere Konstruktoren
public URL(String url) throws MalformedURLException
public URL(String protocol,
           String host,
           String file) throws MalformedURLException
public URL(String protocol,
           String host,
           int port,
           String file) throws MalformedURLException

//ab Java 20: wird aus URI-Objekt konstruirt
public URL toURL()

```

### URL-Verbindung

- zur Kommunikation mit der URL-Ressource
- ist eine High-Level-Verbindung z.B. über Übertragungsprotokolle wie http
- bauen auf Sockets auf 

URL beschreibt eine Ressource. Um darauf zuzugreifen wird Verbindung benötigt. 
Die URL-Verbindungen sind High-Level-Verbindungen, auf dieser Ebene muss man nicht um die Übertragungsprotokolle kümmern. Alle "höheren" Verbindungen bauen aber auf Sockets auf.

- abstrakte Klasse URLConnection

![urlconnection](images/sockets/urlcollection.PNG)

```java
URLConnection URL::openConnection() throws IOException

void connect() throws IOException

Map<String, List<String>> getHeaderFields()
Object getContent() throws IOException

InputStream getInputStream() throws IOException
OutputStream getOutputStream() throws IOException
```

**Zugriff auf URL-Resource**

- Objekt erzeugen: openConnection()
- Eigenschaften festlegen: setXXX(), z.B. setUseCaches
- ggf. wegen geänderter Eigenschaften Verbindung herstellen: connect()

```java
import java.io.*;
import java.net.*;

public class Show_URLText
{ 
  public static void main( String args[] ) 
  { URL url;
    URLConnection connection;
		try
        {   
          url = new URL("http://www..../datei.txt" );
          //url = new URI ("http://www..../datei.txt").toURL();
          connection = url.openConnection();
 		  connection.setUseCaches( false );
          connection.connect();
          InputStream is=connection.getInputStream();
     	  BufferedReader in = new BufferedReader ( new InputStreamReader(is));
		  while( (s = in.readLine() )!= null ) System.out.println(s);
      }
      catch (MalformedURLException e)
      { System.out.println("Url fehlerhaft");
      } 
      catch (IOException e) 
      { System.out.println("Ein/Ausgabefehler");
      } 
    }
  }
```

## Kommunikation über Sockets

### Socket

- alle höhere Verbindungen bauen auf Socket auf
- Socket bildet eine Schnittstelle zwischen Transport- und Anwendungsschicht
- Socket ist ein Verbindungspunkt im Netz: UDP - verbindungslos, TCP - verbindungsorientiert
- bekommt eine IP-Adresse und Port-Nummer
- jeder Kommunikationsbeteiligte (Client und Server) implementiert einen Socket

Socket-Konzept wurde in 80er Jahre an der Berkley-Universität für UNIX entwickelt und hat der Ausbreitung von Internet verholfen.

Socket dient als eine Schnittstelle zwischen Transport- und Anwendungsschicht im TCP/IP Referenzmodell und kann als ein Verbindungspunkt in einem TCP/IP-Netzwerk betrachtet werden (wie eine Art "Steckdose").
Mit Hilfe von Socket können Anwendungen programmiert werden, die über UDP und TCP kommunizieren. UDP-Socket unterstützen eine verbindunglose Kommunikation. Über sie können die Daten nur sendet und empfangen werden.
TCP Socket baut zusätzlich eine Verbindung auf. Die Verbindung bleibt bestehen für die gesamte Dauer der Datenübertragung.
Jeder beteiligte Rechner implementiert einen Socket: derjenige, der die Verbindung initiiert und Daten sendet (einen Client-Socket) und derjenige, der auf eingehende Verbindungen horcht, einen Server-Socket. 


**Port-Nummer**
	System-Ports: 0..1023 ("well-known" System Ports, auch Contact Ports genannt)
	User-Ports: 1024..65535

	z.B. 443 – HTTPS, 80 – HTTP, 20 - FTP	(TCP DATA Port)	


### Verbindungslose Kommunikation – UDP (User Datagram Protocol)

- nur Operationen zum Senden und Empfangen
- Schnell aber unzuverlässig
- Empfänger muss empfangsbereit sein 
- Sender kennt Empfänger (IP-Adresse und Port)
- Empfänger erfährt die Absenderadresse mit dem Empfang der Nachricht (Pakets)
	
![UDP](images/sockets/udp.PNG)

**Datenpaket**
	- Daten
	- IP-Adresse des Ziels
	- Portnummer
	- Absenderadresse

Klasse  **DatagramPacket**

```java
DatagramPacket(byte[] buf, int offset, int length, InetAddress address, int port)
DatagramPacket(byte[] buf, int length)
//aber auch set-Methoden
```

Klassen  **DatagramSocket** und **MulticastSocket**

![UDPKlassen](images/sockets/udpklassen.PNG)

```java
DatagramSocket() throws SocketException	   //any port und local host
DatagramSocket(int port, InetAddress laddr)	 throws SocketException  //spec. local host              			
MulticastSocket(int port) throws IOException
```

### Senden
- void send(DatagramPacket packet) throws IOException
- zuvor das Packet vorbereiten mit Informationen über Empfänger

```java
InetAddress ia;
ia = InetAddress.getByName("sende.wohin.?? " );
int port = 4711;
String s = "Die Botschaft";
byte[] data = s.getBytes();
packet = new DatagramPacket( data, data.length, ia, port );
DatagramSocket socket = new DatagramSocket();
socket.send( packet ); 
```

### Empfangen
- void receive(DatagramPacket packet) throws IOException
- zuvor Paket vorbereiten mit Datenpuffer
- nur Pakete mit bekannter Portnummer werden empfangen

```java
byte[] data = new byte[ 1024 ]; 
DatagramPacket packet = new DatagramPacket( data, data.length );
DatagramSocket socket = new DatagramSocket( 4711 );
socket.receive( packet ); 
```

### Beispiel
```java
/* sende ein UDP - Paket */
import java.io.*;
import java.net.*;

public class UDPSend 
{ 
  public static void main( String args[] ) 
  { 
	  InetAddress iaddr;                           
    int port = 12345;
	  String meldung="Die Meldung";
    try 
    { DatagramSocket d_socket = new DatagramSocket();
      iaddr = InetAddress.getByName("server.informatik.tu-freiberg.de");
      byte[] data = meldung.getBytes();
      DatagramPacket packet;  
      packet = new DatagramPacket(data, data.length, iaddr, port);
      d_socket.send(packet);     
      d_socket.close();
    }
    catch (SocketException e)     {System.out.println(e);}
    catch (UnknownHostException e){System.out.println(e);}
    catch (IOException e)         {System.out.println(e);}
  }
}
```

```java
/* empfange 3 UDP Pakete */
import java.io.*;
import java.net.*;

public class UDPReceive
{ public static void main( String args[] ) 
  {
	 int port = 12345;        
    byte[] buffer = new byte[1024];                
    DatagramPacket packet;
    DatagramSocket d_socket;
    packet = new DatagramPacket(buffer, buffer.length);
    try
    { d_socket = new DatagramSocket(port); 
      for (int i = 0; i < 3; i++)
      { d_socket.receive(packet);
        String s = new String( buffer, 0, packet.getLength() );
        System.out.println( "UDPReceive: from "      
           + packet.getAddress().getHostName() 
           + ":" + packet.getLength() + ":" + packet.getPort() + ":" + s );
        packet.setLength(buffer.length);
      }
      d_socket.close();
    }
    catch (SocketException e) {System.out.println(e);}
    catch (IOException e)     {System.out.println(e);}
  }
}
```

### Multicast (mehrere Empfänger):
 
- Senden per UDP an Klasse D Adressen (224.0.0.0-239.255.255.255)
- Empfangen an Multicast-Adresse/Portnummer mit dem Multicast-Socket 
	```MulticastSocket(int port)```
 
- Beitreten einer Empfängergruppe
   ```void joinGroup(InetAddress addr) throw IOException```

- Empfangen mit receive

- Verlassen der Empfängergruppe
    ```void leaveGroup(InetAddress addr) throw IOException```

### Beispiel
```java
/* empfange 3 UDP Pakete als Multi-Cast*/
import java.io.*;
import java.net.*;
public class UDPMultiCast
{ public static void main( String args[] ) 
  {
	  int port = 12345;        
    byte[] buffer = new byte[1500];    
    DatagramPacket packet = new DatagramPacket(buffer, buffer.length);
    MulticastSocket mc_socket; 				
    InetAddress group;
    try
    { 
      group = InetAddress.getByName("239.255.255.255");
      mc_socket = new MulticastSocket(port);
      mc_socket.joinGroup(group);
      for (int i = 0; i < 3; i++)
      { 
        mc_socket.receive(packet);
        String s = new String( buffer, 0, packet.getLength() );
        System.out.println("MultiCastReceive: from "      
           + packet.getAddress().getHostName() 
           + ":" + packet.getLength() + ":" + packet.getPort() + ":" + s );
        packet.setLength(buffer.length);
      }
      mc_socket.leaveGroup(group);
      mc_socket.close();
    }
    catch (SocketException e | IOException e) {System.out.println(e);}
  }
}
```

## Verbindungsorientierte Kommunikation – TCP (Transmission Control Protocol)

**Verbindungsaufbau und Datenübertragung:**

1. Verbindungsaufbau (unterschiedlich für Client und Server): 
   - Client initiiert die Verbindung zum laufenden Server. 
   - Server wartet an einem speziellen Socket (Server-Socket), stellt einen weiteren Socket zum Kommunizieren zur Verfügung. - -
   - Server-Socket kann für weitere Verbindungsannahmen benutzt werden.
2. Datenübertragung über Input- und Output-Streams
3. Verbindungabbau, erst Client, dann Server

TCP Socket – Kommunikationsendpunkt mit zwei Datenströmen

![TCP](images/sockets/tcp.PNG)

Klassen **Socket** und **ServerSocket**

![TCPKlassen](images/sockets/tcpklassen.PNG)

```java
Socket(InetAddress endpoint, int port) throws IOException
void bind(SocketAddress bindpoint) throws IOException
//ordnet dem Socket eine lokale Adresse zu
void connect(SocketAddress endpoint) throws IOException
//stellt eine Verbindung zu einer entfernten (Server)-Adresse her

InputStream getInputStream() throws IOException
OutputStream getOutputStream() throws IOException

ServerSocket(int port) throws IOException
Socket accept() throws IOException
```

### Beispiel

**Client:**
1. Zieladresse (Objekt) erstellen
2. Socket anlegen (mit Zieladresse und Zielport)
3. Datenströme vom Socket abfragen
4. Kommunizieren über Datenströme mit Hilfe von read() und write() 
5. Datenströme und Socket mit close() schließen

```java
/* sende Nachricht über Socket zum TCP-Server und empfange von dort Antwort */
import java.io.*;
import java.net.*;

public class TCPClient
{ 
  public static void main(String[] args)
  {
    String anfrage= " Anfrage ";
    InetAddress host=InetAddress.getByName(" … ");
	  int port=11111;
    try
    { 
      Socket socket = new Socket(host, port);
      OutputStream zum_server = socket.getOutputStream();
      zum_server.write(anfrage.getBytes() );
      BufferedReader vom_server 
            = new BufferedReader(new InputStreamReader(socket.getInputStream())); 
      String antwort = from_server.readLine();
      System.out.println("Der Server meldet: " + antwort);
      zum_server.close();
      vom_server.close();
      socket.close();
    }
    catch (IOException e)
    		{ System.out.println("Kommunikationsfehler " + e.getMessage());  }
    }
}
```

**Server:**
1. ServerSocket anlegen
2. ServerSocket wartet auf Anfragen 
3. akzeptiert die Anfrage und stellt ein Socket zur Verfügung, ServerSocket kann weitere Anfragen bedienen
4. Datenströme vom (Kommunikations-)Socket abfragen und Kommunizieren mit Hilfe von read() und write() 
5. Datenströme und Sockets (inkl. ServerSocket) mit close() schließen

Server braucht Klassen ServerSocket und Socket, Client nur Socket

```java
/* empfange Nachricht über Socket vom TCP-Client und sende dorthin Antwort */
import java.io.*; 
import java.net.*;

public class TCPServer { 
  public static void main(String[] args) { 
    byte b[] = new byte[64]; 
    String antwort = "Das ist die Antwort vom Server";
	  int port=11111;
    try { 
      ServerSocket s_socket = new ServerSocket (port);
      Socket socket = s_socket.accept();
      System.out.println("verbunden mit: " + socket.getInetAddress().getHostName()
         + " Port: " + socket.getPort() + " local Port: " + socket.getLocalPort() );
      
		  BufferedInputStream vom_client = new BufferedInputStream(socket.getInputStream());
      while (vom_client.available() == 0) ;
      vom_client.read(b);
      System.out.println("Message form client: " + new String(b));

      OutputStream zum_client = s_client.getOutputStream();           
      zum_client.write(antwort.getBytes());

      vom_client.close();
      zum_client.close();
      socket.close();
      s_socket.close(); 
    }
    catch (IOException e) { System.out.println("Fehler bei Kommunikation: " + e); }
  }
}
```

**Nachteil der Single-Thread-Anwendung:**
	es kann die Anfrage nur eines Clients bearbeitet werden, andere Anfragen müssen warten

**Lösung:** 
             Kommunikationssocket an ein Thread oder ExecutorService weiter reichen

```java
/* empfange 3 Nachrichten über Socket vom TCP-Clients und sende jeweils eine Antwort */
/* die Verarbeitung der Nachrichten erfolgt nebenläufig */

import java.io.*;
import java.net.*;

public class TCPMultiServer{
    public static void main(String[] args){
        int port=…;
        try{   
            ServerSocket s_socket = new ServerSocket (port);
            
            for(int anz = 0; anz < 3; anz++){
                Socket socket = s_socket.accept();
                new ServerThread(socket, anz).start();
            }
            s_socket.close(); 
        }
        catch (IOException e) { 
            System.out.println("Fehler bei Kommunikation: " + e); 
        }
    }
}
```
```java
class ServerThread extends Thread{   
    Socket socket;
    public ServerThread( Socket socket, int nummer) {
        this.socket = socket;
        System.out.println("ServerThread " + nummer + " verbunden mit: " 
           + socket.getInetAddress().getHostName() + " Port: " + socket.getPort() );
    }
    public void run() {
        int size;
        byte b[] = new byte[64]; 
        String antwort = "Serverantwort: *";
        try {
            BufferedInputStream vom_client = new BufferedInputStream(socket.getInputStream());
            while ((size = vom_client.available()) == 0) ;
            vom_client.read(b);
            System.out.println("Message form client: " + new String(b));
					  OutputStream zum_client = socket.getOutputStream();
            if (size <= b.length)
                for(int i = 0; i < size; i++)
                   { sleep(300); antwort += ((char)b[i] + "*"); }
            zum_client.write(antwort.getBytes());
					  vom_client.close();
            zum_client.close();
            socket.close();
        }
        catch (Exception e) { e.printStackTrace(); }
    }
}
```

### Beispiel:
```java
public class Server {
  public static void main(String[] args) {
    ServerSocket servers;
    try {
      servers = new ServerSocket(5556);
      while (true){
        Socket socket=servers.accept();
        ServerThread st=new ServerThread(socket);
        st.start();
      }
    } catch (IOException e) { e.printStackTrace(); }
  }
}
```
```java
public class ServerThread extends Thread {
Socket socket;

public ServerThread(Socket socket) { 
  this.socket=socket;
}
public void run() {
  try {
    Scanner sca = new Scanner(socket.getInputStream());
    String s = sca.nextLine();
    System.out.println(s);
        
    PrintWriter pw = new PrintWriter(socket.getOutputStream(),true); //autoflush
    pw.println("Thank you for your message! I will get back to you later.");
    sca.close();
    pw.close();
    socket.close();
    }
    catch (IOException e) {e.printStackTrace();}
  }
}
```

Text zu übertragen – das geht, was geht noch?

### Versenden eines Objektes

- Serialisierung/Deserialisierung - persistent sichern und wiederherstellen. Übertragung übers Netz verwendet das gleiche Mechanismus 
- Java Object Serialization (JOS): Sichern der Objektstruktur im binären Format 
- rekursiver Ablauf unter Berücksichtigung doppelter Zugriffe und zyklischer Abhängigkeiten
- Voraussetzung: Implementierung von Interface Serializable (java.io.Seralizable)


- viele vordefinierte Klassen sind serialisierbar
- nicht serialisierbar:
    - z.B. Thread, Socket und viele Klassen des lang.io-Pakets
    - transient gekennzeichnete Variable
    - Klassenvariablen (static)

Versenden eines Objektes ist im Gesamtkonzept der Serialisierung zu sehen. 
Unter Serialisierung/Deserialisierung versteht man generell persistentes Sichern und Wiederherstellen eines Objektes. Hier geht es um die Standardserialisierung (keine XML-Serialisierung z.B.), d. h. die Objektstruktur wird im binären Format gesichert - das Verfahren wird Java Object Serialization (JOS) genannt. Beim Übertragen über das Netzwerk wird das selbe Mechanismus angewendet.
Zusammen mit Objekten werden auch Unterobjekte gesichert (bzw. übertragen). Beim Speichern wird der Objektbaum resursiv durchlaufen. Dabei werden doppelte Zugriff auf ein Objekt und zyklische Abhängigkeiten erkannt und berücksichtigt.
Die Voraussetzung für die Serialisierung ist die Implementierung in den jeweiligen Klassen des Interface Serializable. Bei vorhandenen vordefinierten Klassen ist das sowieso der Fall, mit Ausnahme von Thread, Socket und vielen Klassen des lang.io-Pakets, den bewusst ausgesparten mit dem Schlüsselwort transient gekennzeichnete Variable (z.B. Passwort) und Klassenvariablen (static) wegen Konflikte.

Bei den eigen definierten Klassen muss zu Serializieren das Interface Serializable implementiert werden. Serializable ist ein marker interface, d.h. es enthält keine Methoden, die zu implementieren wären, markiert nur die Klassen, die serialisiert werden dürfen.

- Interface: ```Serializable``` (marker interface)
- Klassen:
```ObjectOutputStream, ObjectInputStream```
- Serialisierung:
```writeObject(daten)```
falls Objekt nicht serialisierbar: java.io.NotSerializableException
- Deserialisierung:
```readObject()``` liefert Object
falls Klasse nicht verfügbar: java.lang.ClassNotFoundException


**Voraussetzungen:**

- gleiche Klassen müssen vorhanden sein, SerialisierungsID müssen übereinstimmen
- VM muss sie gleich interpretieren können
- beim Lesen Typumwandlung notwendig


```java
import java.io.Serializable;
import java.util.ArrayList;

public class Daten implements Serializable  {

	private static final long serialVersionUID = 1L;
	private ArrayList<String> inhalt;

	public Daten() {
		super();
		inhalt= new ArrayList<String>();
	}

	public ArrayList<String> getInhalt() {
		return inhalt;
	}
}
```
```java
import java.io.IOException;
import java.io.NotSerializableException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class ClientDaten {
public static void main(String[] args) {   
   try {
      Daten daten=new Daten();
      vorbereite(daten);
      Socket socket = new Socket("localhost", 4445);
      ObjectOutputStream oos = new ObjectOutputStream(socket.getOutputStream());
      oos.writeObject(daten);
      ObjectInputStream ois = new ObjectInputStream(socket.getInputStream());
      Daten zurueck=(Daten)ois.readObject();
      for (int i=0;i<zurueck.getInhalt().size();i++) 
          System.out.println(zurueck.getInhalt().get(i));
      ois.close();
      oos.close();
      socket.close();
      } 
      catch (NotSerializableException e1) { e1.printStackTrace();
      } 
      catch (ClassNotFoundException e2) { e2.printStackTrace();
      } 
      catch (IOException e) { e.printStackTrace();
   }
}
public static void vorbereite(Daten daten){ /*…*/ }
}

```
```java
import java.net.ServerSocket;
import java.net.Socket;

public class ServerDaten {
  public static void main(String[] args) {
    try {
      ServerSocket server = new ServerSocket(4445);
      while(true) {
        Socket socket = server.accept();
        new ServerThread(socket).start(); 	   
      }
    } 
    catch (Exception e) {
	    e.printStackTrace();
    }
  }
}
```
```java
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.net.Socket;

public class ServerThread extends Thread {
  private Socket socket;
    
  public ServerThread(Socket socket) {
    super();
    this.socket = socket;
  }
  @Override
  public void run() {
    ObjectInputStream ois;
    try {
      ois = new ObjectInputStream(socket.getInputStream()); 	
      Daten daten = (Daten) ois.readObject();
      veraendere(daten);
      ObjectOutputStream oos = new ObjectOutputStream(socket.getOutputStream());
                oos.writeObject(daten);
      ois.close();
      oos.close();
      socket.close();
      } 
      catch (Exception e) {e.printStackTrace();}
  }
  public void veraendere(Daten daten){ /*…*/ }
}
```

### Verbindungsdaten  

- keine Methoden zum Verbindungsaufbau, nur Verbindungsdaten
- Klasse **InetSocketAddress**
- eine Kombination aus InetAddress und einer Portnummer
- repräsentiert eine Endpunktadresse
- mit getAddress() erhält man InetAddress-Instanz
- verfügt über weitere Methoden: getHostName(), getPort() etc

![inetsocketaddress](images/sockets/inetsocketaddress.PNG)

```java
InetSocketAddress(InetAddress addr, int port)
InetSocketAddress(int port)
InetSocketAddress(String hostname, int port)
```

enthält keine Methoden zum Verbindungsaufbau, nur Verbindungsdaten, aber wozu? 

- Objekte vom Typ InetSocketAddress sind serialisierbar, Socket nicht
- über SocketAddress-Objekte kann z.B. ein Timeout gesetzt werden
- kann als Parameter verwendet werden

```java
InetAddress address = InetAddress.getByName("139.20.17.101");
int port = 12345;
InetSocketAddress socketAddress = new InetSocketAddress(address, port);

InetAddress inetAddress = socketAddress.getAddress();

SocketAddress addr = new InetSocketAddress( host, port );
Socket socket = new Socket();
socket.connect( addr, 100 ); //timeout in 100 ms
```

### TCP-Socket und Threadpool in einer Android-Anwendung
```java
import java.io.PrintWriter;
import java.net.Socket;
import java.util.Scanner;

public class Client {

	public static void main(String[] args) {
		Socket socket;
		try{
		    socket= new Socket("139.20.16.xxx",5556);
		    PrintWriter pw = new PrintWriter(socket.getOutputStream());
		    pw.println("Greetings!");
		    pw.flush();
		    Scanner sca = new Scanner(socket.getInputStream());
		    String s = sca.nextLine();
		    System.out.println(s);
		    pw.close();
		    sca.close();
		    socket.close();
		 }catch(Exception e){
		    System.out.println(e);
		 }	
	}
}
```

```java
public class MainActivity extends AppCompatActivity {
   public class TCPKomm implements Callable<String>{
        String text=null;
        public TCPKomm(String message){
          text=message;
        }     
        @Override
        public String call() throws Exception {
             Socket socket;
             try{
              socket=new Socket("10.0.2.2",5556);
	            //("139.20.16.xxx",5556);             
              PrintWriter pw = new PrintWriter(socket.getOutputStream(),true);
              pw.println(text);
              pw.flush();
                            
              Scanner sca = new Scanner(socket.getInputStream());
              String s = sca.nextLine();
              pw.close();
              sca.close();
              socket.close();
              return s;
            }
            catch(Exception e){
              System.out.println(e);
              return null;
            }
        }
   }
   EditText textedit=null;
   @Override
   protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_main);
      textedit=findViewById(R.id.textedit);
      }
   public void onButtonClick(View view) {
      String message=textedit.getText().toString();
      ExecutorService exec = Executors. newSingleThreadExecutor();
      Future<String> future = exec.submit(new TCPKomm(message));
      try{
        String s=future.get();
        textedit.setText(s);
      } 
      catch (InterruptedException | ExecutionException ex ) {
        ex.printStackTrace();
        } 
      exec.shutdown();
   }
}

```

### TCP vs UDP

**TCP:** Pakete werden nacheinander zugestellt, vollständig, in der richtigen Reihenfolge und nicht doppelt

**UDP:** Pakete werden zugestellt ohne Garantie, dass alle Pakete ankommen, in der richtigen Reihenfolge, jedes einmal. Ggf. Korrektur –, Sicherungsmaßnahmen notwendig 

![tcpvsudp](images/sockets/tcpvsudp.PNG)

## Synchronisation

TCP:  verwendet Sequenznummern

Sequenznummern: triviale Form einer logischen Uhr

**Funktionsschema:**
- Jedem Paket wird eine Sequenznummer zugeordnet und die nächste Sequenznummer mit abgeschickt
- Empfänger kennt aus der Sequenznummer des vorangegangenes Pakets, welche Nachricht dran ist 
- Wird die Nachricht mit der niedrigeren Nummer empfangen, so wird sie verworfen
- Die Nachricht mit der höheren Nummer wird empfangen und in den Zwischenspeicher abgelegt
- Wenn die Nachricht mit der richtigen Nummer angekommen ist, wird Zwischenspeicher abgearbeitet
- Kommt die Nachricht nicht, wird sie nach einer gewissen Zeit von Sender abgefordert
- Nach einer gewissen Anzahl erfolgslosen Rückfragen bricht die Kommunikation mit einer Fehlermeldung ab

**Echtzeituhr:**

- misst physikalische Zeit 
- Synchronisation erfolgt, z.B. mittels Abfrage von Zeitservern und Umrechnungen der Verzögerung durch Übertragungszeit (verschiedene Algorithmen, Standard: Network Time Protokoll)

**Logische Uhr:**

- misst nicht die physikalische Zeit, gib den  Ereignissen einen eindeutigen (logischen) Zeitstempel
- erzeugt streng monoton steigende Werte, um den Ereignissen eine Kasualordnung zuzuweisen


**Verfahren zum Zuweisen von eindeutigen Zeitstempeln an Nachrichten:**

**Lamport-Uhr:**
- Jeder Prozess hat einen Zähler (die Uhr)
- Der aktuelle Stand des Zählers wird an jede Nachricht als Zeitstempel angehängt
- Zähler wird bei jedem Ereignis (Senden und Empfangen) erhöht: wenn eine Nachricht empfangen wird, deren Zeitstempel größer oder gleich dem aktuellen Stand der eigenen Uhr ist, wird der Wert der Uhr um eins erhöht. 
- Nachteil: unbekannt, welche Ereignisse kausal unabhängig (nebenläufig) sind

**Vektoruhr:**
- Berücksichtigt Nebenläufigkeit
- die Uhr jedes Prozesses besteht aus einem Vektor (Array), nicht nur einem Zähler
- Jeder Prozess merkt sich den Zählerstand aller anderen Prozesse
- Der aktuelle Stand der Uhr wird jeder gesendeten Nachricht angehängt 
- Bei jedem Ereignis wird immer nur der eigene Zähler erhöht
- Wird eine Nachricht empfangen, werden aus dem aktuellen und dem empfangenen Vektor elementweise Maxima gebildet

## Transport Layer Security – TLS 

![TLS](images/sockets/tls.png)

Quelle: https://de.wikipedia.org/wiki/Transport_Layer_Security

- Protokoll zur sicheren Datenübertragung über Computernetzwerke, insbesondere im Internet
- Aufgabe: die Echtheit des kontaktierten Servers durch ein Zertifikat zu garantieren und die Verbindung zwischen Client und Server zu verschlüsseln.

**Bestandteile:** 
TLS Handshake - findet Schlüsselaustausch und eine Authentifizierung statt 
TLS Record - verwendet den im Handshake ausgehandelten symmetrischen Schlüssel für eine sichere Datenübertragung – die Daten werden verschlüsselt und mit einem MAC (Message Authentication Code) gegen Veränderungen geschützt übertragen. 

**Anwendung:**
- theoretisch auf alle denkbare Anwendungsprotokolle: HTTP (-Secure), SMTPS, POPS,  IMAPS, …

### TLS-Funktionsweise
Der Client baut eine Verbindung zum Server auf. Beim ersten „Kontakt“ nutzt TLS die asymmetrische Verschlüsselung. 
Der Server schickt als Antwort seinen öffentlichen Schlüssel (public Key) und ein SSL/TLS Zertifikat zur Authentifizierung.
Der Client überprüft die Vertrauenswürdigkeit des Zertifikats und ob der Servername mit dem Zertifikat übereinstimmt. Optional kann sich der Client mit einem eigenen Zertifikat auch gegenüber dem Server authentifizieren. 
Der Client schickt dem Server einen symmetrischen privaten Schlüssel (eine mit dem öffentlichen Schlüssel des Servers verschlüsselte geheime Zufallszahl), oder beide berechnen den (kombinierten) Schlüssel mit dem Diffie–Hellman-(Merkle) -Schlüsselaustausch (DHM-Protokoll zur Schlüsselvereinbarung)
Dieser Schlüssel wird benutzt, um alle Nachrichten zu verschlüsseln und durch einen Message Authentication Code abzusichern

**Symmetrische Verschlüsselung:**
- ein Schlüssel für Verschlüsselung und Entschlüsselung von Daten ("geheimer Schlüssel" )
- schnell und effizient, eignet sich gut für die Verschlüsselung großer Datenmengen
- Herausforderung: der geheime Schlüssel sicher zwischen den Kommunikationspartnern auszutauschen

**Asymmetrische (öffentliche) Verschlüsselung:**
- zwei Schlüssel (öffentlicher und privater Schlüssel): der öffentliche Schlüssel zum Verschlüsseln, der private Schlüssel zum Entschlüsseln von Daten
- ist in der Regel langsamer und rechenintensiver als symmetrische Verschlüsselung
- wird daher oft für den sicheren Austausch von Schlüsseln und die digitale Signierung verwendet, während die eigentliche Datenverschlüsselung mit einem symmetrischen Schlüssel erfolgt

### Ein SSL/TLS-Zertifikat 
- ist eine elektronische Datei, die von einer vertrauenswürdigen Zertifizierungsstelle (Certificate Authority, CA) ausgestellt wird. Das Zertifikat enthält Informationen zur Identität des Servers, Website (Inhaber, Domane, …) , ein Ablaufdatum etc.

- wird von der Zertifizierungsstelle digital signiert, um seine Echtheit zu gewährleisten. Damit wird sicher gestellt, dass es nicht gefälscht oder manipuliert wurde.

- Die Zertifikate werden bei Zertifizierungsstellen (ein Unternehmen, eine Non-Profit-Organisation oder eine Behörde ) beantragt. Weltweit gibt es weit über 700 Zertifizierungsstellen. 

- Zertifizierungsstellen überprüfen und bestätigen die Identität des Antragstellers. Die Zertifizierungsdienstanbieter unterliegen der Aufsicht der Bundesnetzagentur.

- Es gibt insgesamt drei Zertifikatstypen (Domain-Validated-Zertifikat – DV, Organisation-Validation-Zertifikat – OV, Extended-Validation-Zertifikat – EV), die sich durch einen unterschiedlichen Prüfaufwand bei der Zertifizierung unterscheiden und so eine entsprechend unterschiedliche Echtheitsstufe garantieren.

- TLS verwendet Zertifizierungsinstanzen nach X.509-Internet-Standard. Die Zertifikate koppeln eine Identität an einen öffentlichen Schlüssel, der zur Authentifizierung und Verschlüsselung verwendet wird.

s. auch https://www.elektronik-kompendium.de/sites/net/1706131.htm

Die meisten Webbrowser und Betriebssysteme erhalten eine vordefinierten Liste von vertrauenswürdigen Zertifizierungsstellen. Legt der Server ein SSL/TLS-Zertifikat, das von einer dieser Stellen ausgestellt wurde, wird die Verbindung als sicher betrachtet. Andernfalls zeigt der Browser eine Warnung an.
Hosting-Anbieter für Websites oder Cloud-Plattform- Betreiber bieten ggf. integrierte Funktionen zur Beschaffung und Verwaltung von SSL/TLS-Zertifikaten. 

![tubafzertifikat](images/sockets/tubafzertifikat.png)

GEANT Trusted Certificate Services des Deutschen Forschungsnetzes
https://www.pki.dfn.de/geant-trusted-certificate-services/



