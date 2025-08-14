# FMS APIs – Payload and Responses

---

## 📡 Realtime APIs

<details>
<summary><b>1. POST /filters/real-time/preview</b></summary>

**Payload**:
```json
{
  "store": "main-qa-store",
  "app": "hs",
  "entity": "products",
  "filter": {
    "field": "id",
    "operator": "=",
    "value": "9740002099489"
  },
  "columns": ["id", "title"]
}
```

**Response**:
```json
{
  "query": "id:9740002099489",
  "result": [
    {
      "id": "gid://shopify/Product/9740002099489",
      "title": "VANS |AUTHENTIC | LO PRO | BURGANDY/WHITE"
    }
  ]
}
```
</details>

---

<details>
<summary><b>2. OPTIONS /filters/real-time/{entity}</b></summary>

**Payload**:
```
entity → OPTIONS [products, collections, variants, order, publications, location, inventory_levels]
```

**Response**:
```json
{
  "Fields": [
    {
      "name": "barcode",
      "label": "Barcode"
    },
    {}
  ]
}
```
</details>

---

## 🕰 Historical APIs

<details>
<summary><b>1. POST /filters/historical/preview</b></summary>

**Payload**:
```json
{
  "entity": "products",
  "store": "main-qa-store",
  "filter": {
    "field": "id",
    "operator": "=",
    "value": "9740002099489"
  },
  "joins": [
    {
      "columns": ["quantity"],
      "left_on": "id",
      "right_on": "product_id",
      "table": "orders"
    }
  ],
  "columns": ["id", "title"]
}
```

**Response**:
```json
{
  "query": "[(col(\"id\")) == (\"9740002099489\")]",
  "result": [
    {
      "id": "9740002099489",
      "title": "VANS |AUTHENTIC | LO PRO | BURGANDY/WHITE"
    }
  ]
}
```
</details>

---

<details>
<summary><b>2. OPTIONS /filters/historical/{entity}</b></summary>

**Payload**:
```
entity → OPTIONS [collections, inventory_levels, locations, orders, productVariants, products, ga]
```

**Response**:
```json
{
  "additionalProp1": [
    {
      "name": "string",
      "label": "string",
      "placeholder": "string",
      "defaultOperator": {
        "name": "=",
        "label": "string"
      },
      "inputType": "number",
      "valueEditorType": "checkbox",
      "operators": [
        {
          "name": "=",
          "label": "string"
        }
      ],
      "defaultValue": "string",
      "values": ["string"],
      "comparator": "groupNumber",
      "groupNumber": "string",
      "valueSources": ["string"]
    }
  ]
}
```
</details>
