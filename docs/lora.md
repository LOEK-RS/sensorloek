# Grundlagen LoRa


**LoRaWAN** steht für Long Range Wide Area Network

**LoRa** ist die Übertragungstechnik
**LoRaWAN** ist das Netzwerkprotokol

LoRaWAN kann man sich als so etwas ähnliches wie WLAN vorstellen. Daten werden über bestimmte Wellenlängen gesendet und empfangen.
In Europa sind wir in der Regel für die übertragung per LoRa bei 868 Mhz. Zum vergleich: WLAN läuft über 2400 Mhz bzw. 5000 Mhz.



## Gerätespezifikation

Jedes LoRa fähige Gerät besitzt eine AppEUID/JoinEUID, eine DevEUID und einem AppKey.

Die **DevEUID** ist quasi die MAC Adresse des Geräts, also eine Identifizierungsnummer mit der das Gerät eindeutig zugeordnet werden kann.

Die **AppEUID/JoinEUID** ist die Identifikation des Servers der für die Over the air activation zuständig ist. Der Server nutzt diesen Schlüssel um im Netz das Richtige übertragungsformat für das Gerät zu finden. Ein Temperatursensor hat andere Anforderungen als ein Feinstaubmesser.

Der **AppKey** wird für die Entschlüsselung der eigentlichen Nachricht verwendet.

Die DevEUID und die AppEUID sind öffentlich, aber die Nachricht kann nur gelesen werden wenn auch die AppKey bekannt ist.

Siehe hier: [https://stackoverflow.com/questions/54096980/lorawan-deveui-appeui-and-appkey](https://stackoverflow.com/questions/54096980/lorawan-deveui-appeui-and-appkey)





## Was verschicken wir da eigentlich?

Sehr viel Protokollspezifikation + Payload


![http://www.techplayon.com/wp-content/uploads/2018/10/LoRa-Call3-1-730x415.png](http://www.techplayon.com/wp-content/uploads/2018/10/LoRa-Call3-1-730x415.png)


### Payload

Die Payload ist die eigentliche Nachricht die wir verschicken wollen. Diese kann eine maximale größe von 222 Byte haben.
Bei der [Sensebox](sensebox.md) beispielsweise wollen wir folgende Nachricht verschicken:

```
{
  "luminosity_3": 71,
  "relative_humidity_2": 59,
  "temperature_1": 24
}
```


### Cayenne LPP

Um möglichst viel Inhalt in die 222 Byte zu packen sollten/müssen Nachrichten codiert und komprimiert werden.
Das kann man entweder manuel erledigen, die Geräte (wie das [TEK766](tek766.md)) erledigen das intern wie der Hersteller es vorgibt, oder man nutzt standardisierte Protokolle wie was **Cayenne** **L**ow **P**ower **P**ayload.



Komprimiert Payload um möglichst effizient versendet werden zu können

