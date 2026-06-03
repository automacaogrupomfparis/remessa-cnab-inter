# CNAB 240 — Gerador de Pagamentos Pix
### Inter Empresas · Layout v1.21

Ferramenta web local para geração de arquivos CNAB 240 (`.REM`) a partir de planilhas Excel ou CSV.
Funciona 100% no navegador — **nenhum dado é enviado para servidores.**

---

## 🚀 Como usar

1. Acesse a ferramenta pelo GitHub Pages (link no topo do repositório)
2. Selecione a empresa desejada
3. Importe sua planilha `.xlsx` ou `.csv`
4. Clique em **Gerar arquivo CNAB 240**
5. Faça upload do arquivo `.REM` no Inter Empresas

---

## 📋 Formato da planilha

| Coluna | Obrigatório | Exemplo |
|--------|-------------|---------|
| `nome_favorecido` | ✅ | JOAO DA SILVA |
| `tipo_chave` | ✅ | email / telefone / cpf_cnpj / aleatoria / dados_bancarios |
| `chave_pix` | ✅ | joao@email.com |
| `cpf_cnpj_favorecido` | ✅ | 12345678901 (só números) |
| `valor` | ✅ | 150.00 |
| `data_pagamento` | ✅ | 02062026 (DDMMAAAA) |
| `referencia` | ❌ | REF001 |

> Baixe a planilha modelo clicando em **"Baixar planilha modelo"** na ferramenta.

---

## 🏢 Adicionar nova empresa

Na ferramenta, clique em **"+ adicionar"** ao lado das empresas.
A nova empresa fica salva no navegador (localStorage).

Para adicionar permanentemente no código, edite o arquivo `index.html`
e adicione um objeto no array `empresas`:

```js
{
  id: 'profi',
  nome: 'PROFI EMPRESA LTDA',
  cnpj: '00000000000000',
  conta: '00000000',
  dv: '0',
  rua: 'RUA EXEMPLO',
  numero: '100',
  bairro: 'BAIRRO',
  cidade: 'CIDADE',
  uf: 'UF',
  cep: '00000000'
}
```

---

## ⚙️ Publicar no GitHub Pages (passo a passo)

### 1. Criar repositório no GitHub
1. Acesse [github.com](https://github.com) e faça login
2. Clique em **New repository**
3. Nome: `cnab-generator` (ou qualquer nome)
4. Marque **Public**
5. Clique em **Create repository**

### 2. Fazer upload do arquivo
1. No repositório criado, clique em **Add file → Upload files**
2. Arraste o arquivo `index.html`
3. Clique em **Commit changes**

### 3. Ativar GitHub Pages
1. Vá em **Settings → Pages**
2. Em **Source**, selecione: `Deploy from a branch`
3. Branch: `main` / Folder: `/ (root)`
4. Clique em **Save**

### 4. Acessar a ferramenta
Após ~1 minuto, acesse:
```
https://SEU-USUARIO.github.io/cnab-generator/
```

---

## 🔒 Segurança

- Todo o processamento é feito **localmente no navegador**
- Nenhum dado (CNPJ, conta, valores) é enviado para servidores
- O arquivo `.REM` é gerado e baixado direto no seu computador
- Pode ser usado sem internet (basta abrir o `index.html` localmente)

---

## 📄 Conformidade

Gerado conforme **Manual CNAB 240 Pagamentos — Inter Empresas v1.21 (10/02/2026)**
- Segmento A (obrigatório) — dados do pagamento
- Segmento B (obrigatório) — chave Pix / dados bancários
- Forma de lançamento `45` = Transferência via Pix
- Arquivo nomeado no padrão `CI240_001_NNNNNNN.REM`
