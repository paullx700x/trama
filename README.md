# Trama

Editor colaborativo **local-first** sem backend obrigatório. O objetivo é demonstrar sincronização, reconciliação e comportamento offline sem esconder a lógica atrás de uma biblioteca pesada.

## Arquitetura

Cada alteração vira uma operação com versão `[relógio Lamport, clientId]`. Réplicas aplicam a maior versão para cada título/bloco. O documento é persistido em `localStorage` e abas abertas sincronizam por `BroadcastChannel`.

## Recursos
- edição em blocos;
- persistência local;
- sincronização entre abas;
- modo offline com fila de operações;
- reconexão e envio da fila;
- snapshots entre clientes;
- resolução determinística de conflitos;
- painel de estado distribuído.

> Para colaboração entre máquinas diferentes, a mesma camada de operações pode ser transportada por WebRTC/WebSocket sem mudar o modelo de dados.
