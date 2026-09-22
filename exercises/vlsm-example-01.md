# VLSM – Beispiel 01

## Aufgabenstellung

Gegeben ist das Netzwerk:

`192.168.1.0/24`

Es sollen vier Netzwerke eingerichtet werden:

| Netzwerk | Benötigte Hosts |
|---|---:|
| Netz 1 | 8 |
| Netz 2 | 125 |
| Netz 3 | 15 |
| Netz 4 | 4 |

## Vorgehensweise

Bei VLSM werden die benötigten Netzwerke nach ihrer Größe sortiert.

Das größte benötigte Netzwerk wird zuerst eingeplant.

## Lösung

Bei VLSM werden die benötigten Netzwerke zunächst nach der Anzahl der benötigten Hosts sortiert.

| Netzwerk | Benötigte Hosts |
|---|---:|
| Netz 1 | 125 |
| Netz 2 | 15 |
| Netz 3 | 8 |
| Netz 4 | 4 |

### 1. Netzwerk – 125 Hosts

Benötigt werden mindestens 125 nutzbare Host-Adressen.

Da zwei Adressen für Netz-ID und Broadcast reserviert sind:

`125 + 2 = 127`

Die nächste Zweierpotenz ist:

`2^7 = 128`

Damit werden 7 Host-Bits benötigt.

Präfix:

`32 - 7 = /25`

Subnetzmaske:

`255.255.255.128`

Netzwerk:

`192.168.1.0/25`

Netz-ID:

`192.168.1.0`

Erster Host:

`192.168.1.1`

Letzter Host:

`192.168.1.126`

Broadcast:

`192.168.1.127`

---

### 2. Netzwerk – 15 Hosts

Benötigt werden:

`15 + 2 = 17`

Die nächste Zweierpotenz ist:

`2^5 = 32`

Damit werden 5 Host-Bits benötigt.

Präfix:

`32 - 5 = /27`

Subnetzmaske:

`255.255.255.224`

Das nächste freie Subnetz beginnt nach `192.168.1.127`.

Netzwerk:

`192.168.1.128/27`

Netz-ID:

`192.168.1.128`

Erster Host:

`192.168.1.129`

Letzter Host:

`192.168.1.158`

Broadcast:

`192.168.1.159`

---

### 3. Netzwerk – 8 Hosts

Benötigt werden:

`8 + 2 = 10`

Die nächste Zweierpotenz ist:

`2^4 = 16`

Damit werden 4 Host-Bits benötigt.

Präfix:

`32 - 4 = /28`

Subnetzmaske:

`255.255.255.240`

Das nächste freie Subnetz beginnt nach `192.168.1.159`.

Netzwerk:

`192.168.1.160/28`

Netz-ID:

`192.168.1.160`

Erster Host:

`192.168.1.161`

Letzter Host:

`192.168.1.174`

Broadcast:

`192.168.1.175`

---

### 4. Netzwerk – 4 Hosts

Benötigt werden:

`4 + 2 = 6`

Die nächste Zweierpotenz ist:

`2^3 = 8`

Damit werden 3 Host-Bits benötigt.

Präfix:

`32 - 3 = /29`

Subnetzmaske:

`255.255.255.248`

Das nächste freie Subnetz beginnt nach `192.168.1.175`.

Netzwerk:

`192.168.1.176/29`

Netz-ID:

`192.168.1.176`

Erster Host:

`192.168.1.177`

Letzter Host:

`192.168.1.182`

Broadcast:

`192.168.1.183`

## Ergebnis

| Netzwerk | CIDR | Netz-ID | Hostbereich | Broadcast |
|---|---|---|---|---|
| 125 Hosts | /25 | 192.168.1.0 | .1 – .126 | .127 |
| 15 Hosts | /27 | 192.168.1.128 | .129 – .158 | .159 |
| 8 Hosts | /28 | 192.168.1.160 | .161 – .174 | .175 |
| 4 Hosts | /29 | 192.168.1.176 | .177 – .182 | .183 |

## Subnetzaufteilung

Das ursprüngliche Netzwerk `192.168.1.0/24` wurde mithilfe von VLSM in vier unterschiedlich große Subnetze aufgeteilt.

```text
192.168.1.0/24
│
├── 192.168.1.0/25
│   └── 125 Hosts
│
├── 192.168.1.128/27
│   └── 15 Hosts
│
├── 192.168.1.160/28
│   └── 8 Hosts
│
└── 192.168.1.176/29
    └── 4 Hosts
