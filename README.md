# 📘 Sistema de Disseny de Sistemes (UML)

Aquest projecte conté diversos diagrames UML generats amb PlantUML per representar casos d'ús i seqüències de diferents sistemes, com ara una biblioteca, un sistema de metro i un sistema de compra de skins. Cada secció inclou el codi UML, una breu explicació i una imatge de resultat (que has de generar amb PlantUML).

---

## 🟩 Cas d'ús: Sistema de Venda de Bitllets de Metro

Aquest diagrama mostra com un viatger pot comprar i validar bitllets, aplicar descomptes i fer pagaments a través del sistema de venda.

### 📄 Codi UML
```plantuml
@startuml
left to right direction

actor Viatger << ciutadà >> #lightblue;line:lightblue;text:lightblue
actor Administrador << treballador TMB>>
actor SistemaBancari #lightblue

Administrador -left-|> Viatger

rectangle "Sistema de Venda de Bitllets de Metro" {
    usecase "Comprar Bitllet" as UC1 #green
    usecase "Seleccionar Mètode de Pagament" as UC2 #lightgreen
    usecase "Processar Pagament" as UC3 #lightblue
    usecase "Aplicar Descompte de Transport" as UC4
    usecase "Validar Bitllet" as UC5
    usecase "Anul·lar Bitllet" as UC6 #red
    usecase "Consultar Vendes" as UC7
}

Viatger -[#lightgreen]-> UC1
Viatger --> UC5
Viatger -[#red]-> UC6

Administrador -[#red]-> UC6
Administrador --> UC7

UC1 .[#black].> UC2 : <<include>>
UC2 .[#darkgreen].> UC3 : <<include>>
UC1 .[#darkblue].> UC4 : <<extend>>
UC6 .[#darkred].> UC1 : <<extend>>

SistemaBancari -[#darkgreen]-> UC3
@enduml
