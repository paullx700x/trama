# Trama

Editor colaborativo **local-first** com transportes reais e sem modo de rede simulado.

## Arquitetura

Cada alteração vira uma operação com versão `[relógio Lamport, clientId]`. Réplicas aplicam a maior versão para cada título/bloco. O documento é persistido em `localStorage`.

### Transporte local

Abas reais do mesmo navegador/dispositivo sincronizam por `BroadcastChannel`.

### Transporte remoto opcional

É possível informar um endpoint `ws://` ou `wss://` real. Quando o WebSocket abre, operações e snapshots passam a ser enviados ao servidor. Se o socket cair, somente as operações destinadas ao transporte remoto ficam em fila e são enviadas depois da reconexão.

O servidor precisa retransmitir as mensagens JSON entre clientes da mesma sala. O Trama não finge uma conexão remota quando nenhum servidor está configurado.

## Recursos

- edição em blocos;
- persistência local real;
- sincronização entre abas por BroadcastChannel;
- WebSocket remoto opcional;
- fila baseada no estado real do WebSocket;
- snapshots entre clientes;
- relógio Lamport;
- resolução determinística de conflitos;
- presença local observada por mensagens reais.

O estado inicial é vazio; não há colaboradores, documento ou eventos fictícios pré-carregados.