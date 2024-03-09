# hunter_mosaic_scenario

L'attualmente unica sottocartella presente contiene lo scenario Mosaic, opportunamente modificato, con cui sono stati svolti i test.

# Principali peculiarità

## Mappa custom
La mappa è costituita soltanto da un lungo rettilineo (due nodi e un arco).

### EXTRA: modificare la mappa
1) modificare ./sumo/Scaled_Rettilineo_Test_1.net.xml con netedit (in caso di sostanziali modifiche, verificare l'impatto che tali modifiche avranno sulle route che avranno i veicoli, contenute nel file ./sumo/Scaled_Rettilineo_Test_1.rou.xml).
2) eliminare il vecchio database (./sumo/Scaled_Rettilineo_Test_1.db)
3) creare un nuovo database a partire dalla mappa
$ cd sumo
$ ./scenario-convert-23.1.jar --sumo2db -i Scaled_Rettilineo_Test_1.net.xml
4) aggiungere le route al database
$ ./scenario-convert-23.1.jar --sumo2db -d Scaled_Rettilineo_Test_1.db -i Scaled_Rettilineo_Test_1.rou.xml
5) copiare il nuovo database ./sumo/Scaled_Rettilineo_Test_1.db nella cartella da cui Mosaic lo leggerà (sovrascrivendo il vecchio) ./application/Scaled_Rettilineo_Test_1.db

## Passo di simulazione 20ms / 0.02s / 50 Hz
Ricordare che eventuali modifiche vanno fatte in entrambi i file:
- ./sumo/sumo_config.json -> in millisecondi
- ./sumo/Scaled_Rettilineo_Test_1.sumocfg -> in secondi

## Mosaic Applications RosVehicleApp e LeadingVehicle_CamSendingApp
Entrambe le applicazioni (il cui sorgente java si può trovare nel repository https://github.com/alexmonaco16/Mosaic2RosBridge ) si trovano già compilate nel file ./application/Mosaic2RosBridge-0.0.1.jar

## Simulazione di rete
Attualmente, come simulatore di rete viene usato SNS (il più semplice). Nel suo file di configurazione ./sns/sns_config.json si può notare come si sia impostato un funzionamento ideale con raggio di comunicazione praticamente infinito e loss probability 0.0%.



