---
license: mit
tags:
  - translation
  - nlp
  - sanskrit
  - english
  - transformers
  - fine-tuned
language:
  - sa
  - en
datasets:
  - rahular/itihasa
model-index:
  - name: Sanskrit-English Translator (IndicTrans2)
    results: []
---

# Sanskrit → English Translator (Fine-tuned IndicTrans2)

 This is a fine-tuned [IndicTrans2](https://huggingface.co/ai4bharat/indictrans2-en) model that translates classical Sanskrit texts (like Ramayana and Mahabharata) into English.

- Fine-tuned on `rahular/itihasa` (~93k shloka pairs)
- Input: Devanagari Sanskrit
- Output: Natural English translations
- Base model: `ai4bharat/indictrans2-en`

---

## 🔧 Usage (Python)

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("ayushvjha/Sanskrit-English-Translator")
model = AutoModelForSeq2SeqLM.from_pretrained("ayushvjha/Sanskrit-English-Translator")

inputs = tokenizer("कौशल्यासुप्रजा राम पूर्वा सन्ध्या प्रवर्तते", return_tensors="pt")
output = model.generate(**inputs)
print(tokenizer.decode(output[0], skip_special_tokens=True))
