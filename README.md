Desafio-entrevista-arquitetosolucoes
Projeto de arquitetura escalável com monitoramento e observabilidade

## Sistema de Controle de Lançamentos e Consolidação Diária

## Descrição do Projeto
Este projeto tem como objetivo fornecer uma solução para o controle de lançamentos financeiros (débitos e créditos) e a geração de relatórios consolidados de saldo diário.  
A arquitetura foi desenhada com foco em escalabilidade, resiliência, segurança e facilidade de manutenção, aplicando boas práticas de desenvolvimento e arquitetura de software.

## Objetivos Principais

- Registrar lançamentos diários de forma segura e eficiente.
- Consolidar o saldo diário a partir dos lançamentos registrados.
- Garantir alta disponibilidade e baixa latência dos serviços.
- Disponibilizar APIs padronizadas para integração com sistemas externos.
- Implementar observabilidade e monitoramento para acompanhar a saúde do sistema.

## Arquitetura da Solução

A solução foi estruturada com base em microsserviços para proporcionar desacoplamento, escalabilidade e resiliência. Cada serviço tem responsabilidade própria, permitindo evolução e manutenção independentes.

### Componentes Principais

- **API Gateway**: Responsável por autenticação, autorização, roteamento e rate limiting.
- **Lançamentos Service**: Serviço responsável por criar, atualizar, consultar e excluir lançamentos financeiros. Publica eventos para o serviço de consolidação.
- **Consolidado Service**: Consome eventos de lançamentos, calcula o saldo diário consolidado e disponibiliza relatórios via API.
- **Banco de Dados**: Armazena os lançamentos e os saldos consolidados.
- **Cache (opcional)**: Redis utilizado para consultas rápidas de saldos consolidados.
- **Observabilidade e Logs**: Monitoramento e auditoria com Prometheus, Grafana e ELK Stack.

## Diagrama de Componentes
O diagrama apresenta a interação entre os serviços principais, banco de dados, cache, gateway e camada de observabilidade.

<img width="801" height="711" alt="Diagrama_componentes drawio" src="https://github.com/user-attachments/assets/0715ddb1-b202-401a-a764-ecf91d1a3ab3" />








## Tecnologias Utilizadas

| Componente        | Tecnologia            | Finalidade                                |
|-------------------|----------------------|------------------------------------------|
| Backend          | Node.js / Spring Boot | Desenvolvimento dos microsserviços      |
| API Gateway      | Kong / Nginx         | Roteamento, autenticação e limites      |
| Banco de Dados   | PostgreSQL / MySQL   | Persistência dos dados                  |
| Cache           | Redis                | Otimização de consultas                |
| Mensageria      | Kafka / RabbitMQ     | Comunicação assíncrona entre serviços  |
| Observabilidade | Prometheus / Grafana | Monitoramento de métricas             |
| Logs            | ELK Stack           | Centralização de registros e auditoria |
| Containerização | Docker + Compose    | Orquestração e empacotamento           |
