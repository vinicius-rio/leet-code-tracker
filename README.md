# Garagem Ford Fiesta 2007 — Zetec Rocam

🔗 **Acesse o site:** [My Garage](https://vinicius-rio.github.io/my-garage/)

## 📌 Sobre o projeto

Este projeto é um site interativo e responsivo criado para documentar o funcionamento do **Ford Fiesta Hatch 2007 1.6 Zetec Rocam 8V Flex** e também servir como uma **garagem digital** para controle de manutenção do veículo.

A aplicação combina uma documentação visual para leigos sobre motor, consumo, sistema eletrônico, manutenção preventiva e diagnóstico com uma área autenticada para registrar e acompanhar manutenções reais do carro.


## 🚗 Veículo documentado

- **Modelo:** Ford Fiesta Hatch
- **Ano:** 2007
- **Motor:** Zetec Rocam 1.6 8V Flex
- **Cilindrada:** 1.598 cm³
- **Potência aproximada:** 111 cv no etanol / 105 cv na gasolina
- **Torque aproximado:** 15,8 kgfm no etanol / 14,8 kgfm na gasolina
- **Alimentação:** Injeção eletrônica multiponto
- **Comando:** 8 válvulas
- **Tração:** Dianteira


## 🧠 Objetivo

O objetivo do projeto é permitir que o proprietário do veículo:

1. Entenda melhor o funcionamento mecânico e eletrônico do carro.
2. Consulte informações básicas de manutenção preventiva.
3. Registre manutenções realizadas.
4. Acompanhe próximas trocas por quilometragem e data.
5. Acesse os dados em qualquer dispositivo, sem depender do navegador local.
6. Proteja os registros com login e banco de dados em nuvem.


## ✨ Funcionalidades principais

### 📘 Guia técnico para leigos

O site possui seções explicativas sobre:

- Motor Zetec Rocam 1.6 8V;
- Bloco, pistões, virabrequim, cabeçote, cárter e correia dentada;
- Ciclo de combustão em 4 tempos;
- Consumo com gasolina e etanol;
- Sistema eletrônico;
- Sensores;
- Ignição;
- Injeção eletrônica;
- Alternador, bateria, motor de partida, fusíveis e relés;
- Manutenção preventiva;
- Diagnóstico por sintomas;
- Quiz interativo.

### 🛠️ Área “Meu carro”

A área de garagem permite:

- Login com e-mail e senha;
- Cadastro de veículo;
- Atualização da quilometragem atual;
- Cadastro de manutenções;
- Edição de manutenções;
- Exclusão de manutenções;
- Registro de:
  - nome da manutenção;
  - data da última troca;
  - km da última troca;
  - intervalo por km;
  - intervalo por meses;
  - observações;
- Cálculo automático de vencimento por km e por data;
- Status automático da manutenção:
  - em dia;
  - atenção;
  - vencida.


## 🧰 Tecnologias utilizadas

### Front-end

- **HTML5**
- **CSS3**
- **JavaScript Vanilla**
- Layout responsivo para desktop, tablet e celular
- GitHub Pages para hospedagem estática

### Back-end / Banco de dados

- **Supabase**
- **Supabase Auth**
- **PostgreSQL**
- **Row Level Security (RLS)**


## 🏗️ Arquitetura

```text
GitHub Pages
   ↓
HTML + CSS + JavaScript
   ↓
Supabase Auth
   ↓
Supabase PostgreSQL
   ↓
Row Level Security por usuário
```

O projeto não usa servidor próprio. O front-end é estático e o Supabase fornece autenticação, banco de dados e API.


## 🔐 Segurança

A aplicação utiliza autenticação via Supabase Auth e políticas de **Row Level Security** no banco.

Isso significa que cada usuário autenticado só pode acessar, inserir, editar ou excluir os próprios dados.

As tabelas usam o campo `user_id` associado ao usuário autenticado por `auth.uid()`.

### Cuidados importantes

- Nunca exponha a `service_role key` no HTML.
- Use apenas a `anon public key` no front-end.
- Mantenha o RLS ativado.
- Não deixe cadastro público aberto se o app for de uso pessoal.
- Evite armazenar imagens ou arquivos grandes se quiser manter custo zero.


## 🗄️ Estrutura do banco

### Tabela `vehicles`

Armazena os dados principais do veículo.

| Campo | Descrição |
|
| `id` | Identificador único do veículo |
| `user_id` | ID do usuário dono do veículo |
| `name` | Nome do veículo |
| `model_year` | Ano/modelo |
| `engine` | Motorização |
| `current_km` | Quilometragem atual |
| `created_at` | Data de criação |
| `updated_at` | Data da última atualização |

### Tabela `maintenance_records`

Armazena os registros de manutenção.

| Campo | Descrição |
|
| `id` | Identificador único da manutenção |
| `user_id` | ID do usuário dono do registro |
| `vehicle_id` | Veículo relacionado |
| `service_name` | Nome da manutenção |
| `service_km` | Quilometragem da última troca |
| `service_date` | Data da última troca |
| `interval_km` | Intervalo recomendado em km |
| `interval_months` | Intervalo recomendado em meses |
| `notes` | Observações |
| `created_at` | Data de criação |
| `updated_at` | Data da última atualização |


## 🚀 Como executar o projeto

### 1. Clonar o repositório

```bash
git clone https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
cd NOME-DO-REPOSITORIO
```

### 2. Criar projeto no Supabase

1. Acesse o Supabase.
2. Crie um novo projeto.
3. Copie:
   - Project URL;
   - anon public key.

### 3. Criar as tabelas

No painel do Supabase:

```text
SQL Editor → New query
```

Cole e execute o script SQL do projeto.

### 4. Configurar o HTML

No arquivo HTML principal, localize:

```js
const SUPABASE_URL = 'COLE_AQUI_A_PROJECT_URL_DO_SUPABASE';
const SUPABASE_ANON_KEY = 'COLE_AQUI_A_ANON_PUBLIC_KEY_DO_SUPABASE';
```

Substitua pelos dados do seu projeto Supabase.

### 5. Publicar no GitHub Pages

No GitHub:

```text
Settings → Pages
```

Selecione:

```text
Branch: main
Folder: /root
```

Depois salve e aguarde a URL ser publicada.


## ⚙️ Configuração recomendada no Supabase

Para uso pessoal, recomenda-se:

- manter o projeto no plano gratuito;
- não adicionar cartão de crédito;
- não usar Supabase Storage para arquivos pesados;
- desativar cadastro público se possível;
- criar manualmente o usuário principal;
- manter RLS ativado nas tabelas.


## 📱 Responsividade

O layout foi adaptado para funcionar em:

- computadores;
- notebooks;
- tablets;
- celulares.

A navegação mobile possui menu compacto, os cards se reorganizam em coluna e os elementos interativos se ajustam à largura da tela.


## 🧪 Itens de manutenção acompanhados

O projeto pode acompanhar itens como:

- troca de óleo;
- filtro de óleo;
- filtro de ar;
- filtro de combustível;
- velas de ignição;
- limpeza de injeção;
- limpeza do corpo de borboleta;
- fluido de freio;
- correia dentada;
- alinhamento;
- balanceamento;
- terminais de direção;
- pneus;
- bateria;
- amortecedores;
- qualquer outro item personalizado.


## 📊 Lógica de vencimento

A manutenção pode vencer por dois critérios:

1. **Quilometragem**
   - Exemplo: óleo trocado aos 145.000 km com intervalo de 5.000 km.
   - Próxima troca: 150.000 km.

2. **Data**
   - Exemplo: óleo trocado em 30/05/2026 com intervalo de 6 meses.
   - Próxima troca: 30/11/2026.

O sistema calcula automaticamente o status com base nesses critérios.


## 🧾 Possíveis melhorias futuras

- Upload de notas fiscais;
- Exportação para CSV;
- Histórico financeiro de gastos;
- Dashboard com custo total por mês;
- Alertas por e-mail;
- Cadastro de mais de um veículo;
- Área administrativa;
- Integração com calendário;
- Registro de oficinas e mecânicos;
- Modo somente leitura para consulta pública.


## 📚 Referências

- Ford Brasil — Manuais do proprietário.
- Supabase — Documentação de Auth, Database e Row Level Security.
- PostgreSQL — Documentação oficial sobre políticas de segurança por linha.
- Fichas técnicas públicas do Ford Fiesta Hatch 2007 1.6 Zetec Rocam Flex.


## 👤 Autor

Projeto desenvolvido por **Vinicius Santoro** como uma garagem digital pessoal para acompanhamento e estudo do Ford Fiesta Hatch 2007.


## 📄 Licença

Este projeto é de uso pessoal e educacional.  
