# Trabalho Prático I - Integração de Sistemas de Informação (2026/2027)

- **Autor:** Pedro Gonçalves
- **Número de Estudante:** 26018
- **Curso:** Licenciatura em Engenharia de Sistemas Informáticos (ESI)
- **Unidade Curricular:** Integração de Sistemas de Informação (ISI)
- **Link para o Vídeo de Demonstração:** https://drive.google.com/file/d/1iZo80QdqG8VUEhBP4V9dd4peAP59BBaW/view?usp=sharing
- **Repositório Git:** https://github.com/Pmgg3110/TP1.ISI_26018.git

---

## 📁 Estrutura de Ficheiros

- `26018_doc.pdf`: Relatório técnico final.
- `docker-compose.yml`: Orquestração da infraestrutura (Mosquitto, PostgreSQL, Grafana, Node-RED).
- `README.md`: Documentação e guia de execução do projeto.
- `.gitignore`: Ficheiro com as regras de exclusão para o repositório Git.
- **`pentaho/`**: Pasta contendo as transformações e o Job de orquestração do Pentaho Data Integration (`.ktr`, `.kjb`).
- **`data/`**: Pasta com os ficheiros estáticos de entrada (ex: XML, CSV) e os dados de saída/anomalias gerados pelo ETL.
- **`mosquitto/`**: Pasta com os ficheiros de configuração do broker MQTT.
- **`nodered_data/`**: Pasta de volume do Docker contendo as configurações e fluxos do Node-RED.
- **`logs/`**: Pasta onde são gravados os registos de erros e leituras anómalas do sistema.

---

## 🛠️ Como Executar a Solução

### Pré-requisitos
- **Docker** e **Docker Compose** instalados.
- **Pentaho Data Integration (Spoon)** com o plugin **MQTT Consumer** ativo.

### 1. Iniciar a Infraestrutura de Containers
No terminal, na mesma pasta onde se encontra o ficheiro `docker-compose.yml`, arranca os serviços executando:
```bash
docker compose up -d

(Serviços iniciados: Mosquitto em localhost:1883, PostgreSQL em localhost:5432, Node-RED em localhost:1880 e Grafana em localhost:3000).
2. Ativar a Simulação no Node-RED

    Acede a http://localhost:1880 no teu browser.

    Como a pasta nodered_data já está mapeada, o fluxo de sensores deverá estar disponível.

    Ativa o processo de simulação clicando nos nós de injeção (botões azuis à esquerda dos nós) para começar a gerar telemetria.

3. Executar o Pipeline ETL no Pentaho

    Abre o Pentaho Spoon.

    Acede à pasta pentaho/ e abre o ficheiro do Job principal.

    Clica no botão Run (ícone de play verde). A extração ficará a correr em tempo real à escuta do MQTT.

4. Consultar os Dashboards no Grafana

    Acede a http://localhost:3000 (utilizador: admin / passe: admin).

    Navega até aos Dashboards e abre o painel de Monitorização para acompanhar as métricas em tempo real.
