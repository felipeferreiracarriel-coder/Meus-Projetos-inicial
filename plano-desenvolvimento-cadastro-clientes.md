# Plano de Desenvolvimento – Cadastro de Clientes (Python)

## 1. Visão geral

Sistema de cadastro de clientes em Python que armazena **nome** e **data de nascimento**, com persistência em arquivo e interface via terminal (CLI).

---

## 2. Requisitos funcionais

| ID | Requisito | Descrição |
|----|-----------|-----------|
| RF01 | Cadastrar cliente | Inserir nome e data de nascimento |
| RF02 | Listar clientes | Exibir todos os clientes cadastrados |
| RF03 | Buscar cliente | Buscar por nome ou parte do nome |
| RF04 | Editar cliente | Alterar nome e/ou data de nascimento |
| RF05 | Excluir cliente | Remover cliente do cadastro |
| RF06 | Persistência | Salvar e carregar dados em arquivo |

---

## 3. Regras de negócio

- **Nome**: obrigatório, sem números.
- **Data de nascimento**: obrigatória, formato DD/MM/AAAA, data válida e no passado.
- Cada cliente deve ter um identificador único (ex.: ID numérico ou UUID).

---

## 4. Stack tecnológica

- **Linguagem**: Python 3.8+
- **Persistência**: arquivo JSON ou CSV (sem banco de dados inicial)
- **Interface**: linha de comando (CLI)
- **Validação**: módulo `datetime` e funções próprias

---

## 5. Estrutura do projeto sugerida

```
cadastro-clientes/
├── README.md
├── requirements.txt          # dependências (se houver)
├── main.py                   # ponto de entrada / menu principal
├── models/
│   └── cliente.py            # classe Cliente
├── services/
│   └── cliente_service.py    # lógica de negócio e arquivo
├── utils/
│   └── validadores.py        # validação de nome e data
└── data/
    └── clientes.json         # arquivo de dados (criado em tempo de execução)
```

---

## 6. Modelo de dados

### Cliente

| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | int ou str | Identificador único |
| nome | str | Nome completo |
| data_nascimento | str | Data no formato DD/MM/AAAA |

Exemplo em JSON:

```json
{
  "id": 1,
  "nome": "Maria Silva",
  "data_nascimento": "15/03/1990"
}
```

---

## 7. Fases de desenvolvimento

### Fase 1 – Fundação (MVP)
- [ ] Criar estrutura de pastas e arquivos
- [ ] Implementar classe `Cliente` em `models/cliente.py`
- [ ] Implementar validação de nome e data em `utils/validadores.py`
- [ ] Implementar leitura/gravação em arquivo JSON em `services/cliente_service.py`
- [ ] Menu principal em `main.py`: 1-Cadastrar, 2-Listar, 0-Sair
- [ ] Testar cadastro e listagem com dados salvos em arquivo

### Fase 2 – CRUD completo
- [ ] Opção 3 – Buscar cliente por nome
- [ ] Opção 4 – Editar cliente (por ID ou nome)
- [ ] Opção 5 – Excluir cliente
- [ ] Tratamento de erros (arquivo inexistente, JSON inválido, dados inválidos)

### Fase 3 – Melhorias
- [ ] Cálculo de idade a partir da data de nascimento
- [ ] Ordenação da listagem (por nome ou data)
- [ ] Confirmação antes de excluir
- [ ] Mensagens de sucesso/erro consistentes
- [ ] Documentação no README (como instalar e executar)

### Fase 4 – Opcional
- [ ] Interface gráfica (tkinter ou similar)
- [ ] Migração para SQLite
- [ ] Testes unitários (pytest)

---

## 8. Fluxo do programa (CLI)

1. Iniciar aplicação → carregar clientes do arquivo (se existir).
2. Exibir menu:
   - 1 – Cadastrar cliente
   - 2 – Listar clientes
   - 3 – Buscar cliente
   - 4 – Editar cliente
   - 5 – Excluir cliente
   - 0 – Sair
3. Ao cadastrar/editar: solicitar nome e data de nascimento; validar; salvar e persistir no arquivo.
4. Ao sair: garantir que os dados foram salvos no arquivo.

---

## 9. Validações a implementar

- **Nome**: não vazio; apenas letras, espaços e acentos (opcional: tamanho mínimo/máximo).
- **Data**:
  - Formato DD/MM/AAAA (regex ou `datetime.strptime`).
  - Data existente no calendário.
  - Data não futura.

---

## 10. Cronograma sugerido

| Fase | Atividade | Estimativa |
|------|-----------|------------|
| 1 | MVP (cadastro + listagem + arquivo) | 1–2 dias |
| 2 | Buscar, editar, excluir + erros | 1–2 dias |
| 3 | Idade, ordenação, confirmações, README | 1 dia |
| 4 | Opcionais (GUI, SQLite, testes) | Conforme necessidade |

---

## 11. Entregáveis

- Código fonte organizado conforme a estrutura do item 5
- Arquivo de dados (JSON ou CSV) gerado pela aplicação
- README com instruções de instalação e uso
- Este plano em `plano-desenvolvimento-cadastro-clientes.md`

---

*Documento gerado como parte do plano de desenvolvimento do projeto de cadastro de clientes.*
