# Invoice data processing LLM RAG on CPU with Ollama, LlamaIndex and Weaviate


<a href="https://www.youtube.com/watch?v=tiYQiWWd7rE" target="_blank">Enhancing RAG: LlamaIndex and Ollama for On-Premise Data Extraction</a>

___

## Quickstart

### RAG runs offline on local CPU

1. Install Weaviate local DB with Docker:
   
```
docker compose up -d
```

2. Install the requirements: 

```
pip install -r requirements.txt
```

3. Install <a href="https://ollama.ai">Ollama</a> and pull LLM model specified in config.yml

4. Copy text PDF files to the `data` folder

5. Run the script, to convert text to vector embeddings and save in Weaviate: 

```
python ingest.py
```

6. Run the script, to process data with LLM RAG and return the answer: 

```
python main.py "What is the invoice number value?"
```

Answer:

```json
{
    "invoice_number": 61356291,
    "invoice_date": "09/06/2012",
    "client_name": "Rodriguez-Stevens",
    "client_address": "2280 Angela Plain, Hortonshire, MS 93248",
    "client_tax_id": "939-98-8477",
    "seller_name": "Chapman, Kim and Green",
    "seller_address": "64731 James Branch, Smithmouth, NC 26872",
    "seller_tax_id": "949-84-9105",
    "iban": "GB50ACIE59715038217063",
    "names_of_invoice_items": [
        "Wine Glasses Goblets Pair Clear Glass",
        "With Hooks Stemware Storage Multiple Uses Iron Wine Rack Hanging Glass",
        "Replacement Corkscrew Parts Spiral Worm Wine Opener Bottle Houdini",
        "HOME ESSENTIALS GRADIENT STEMLESS WINE GLASSES SET OF 4 20 FL OZ (591 ml) NEW"
    ],
    "gross_worth_of_invoice_items": [
        66.0,
        123.55,
        8.25,
        14.29
    ],
    "total_gross_worth": "$212,09"
}
```
