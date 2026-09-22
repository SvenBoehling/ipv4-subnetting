# Subnetting – Beispiel 01

## Aufgabenstellung

Gegeben ist das Netzwerk:

`192.168.10.0/24`

Das Netzwerk soll in 4 gleich große Subnetze aufgeteilt werden.

## Gesucht

Für jedes Subnetz sollen bestimmt werden:

- Netz-ID
- Subnetzmaske
- erster Host
- letzter Host
- Broadcast-Adresse

## Vorgehensweise

Da 4 gleich große Subnetze benötigt werden, müssen zunächst ausreichend Bits aus dem Hostanteil ausgeliehen werden.

Für 4 Subnetze werden benötigt:

`2^2 = 4`

Daher werden 2 Bits für die Subnetzbildung verwendet.

Ausgehend von `/24` ergibt sich:

`/24 + 2 = /26`

Die neue Subnetzmaske lautet:

`255.255.255.192`

### Subnetz 1

Netz-ID:

`192.168.10.0`

Erster Host:

`192.168.10.1`

Letzter Host:

`192.168.10.62`

Broadcast:

`192.168.10.63`

---

### Subnetz 2

Netz-ID:

`192.168.10.64`

Erster Host:

`192.168.10.65`

Letzter Host:

`192.168.10.126`

Broadcast:

`192.168.10.127`

---

### Subnetz 3

Netz-ID:

`192.168.10.128`

Erster Host:

`192.168.10.129`

Letzter Host:

`192.168.10.190`

Broadcast:

`192.168.10.191`

---

### Subnetz 4

Netz-ID:

`192.168.10.192`

Erster Host:

`192.168.10.193`

Letzter Host:

`192.168.10.254`

Broadcast:

`192.168.10.255`

## Ergebnis

| Subnetz | CIDR | Netz-ID | Erster Host | Letzter Host | Broadcast |
|---|---|---|---|---|---|
| 1 | /26 | 192.168.10.0 | 192.168.10.1 | 192.168.10.62 | 192.168.10.63 |
| 2 | /26 | 192.168.10.64 | 192.168.10.65 | 192.168.10.126 | 192.168.10.127 |
| 3 | /26 | 192.168.10.128 | 192.168.10.129 | 192.168.10.190 | 192.168.10.191 |
| 4 | /26 | 192.168.10.192 | 192.168.10.193 | 192.168.10.254 | 192.168.10.255 |
