# Sanskrit → English Translator (Fine-tuned IndicTrans2)

🚀 This repository contains a fine-tuned [IndicTrans2](https://huggingface.co/ai4bharat/indictrans2-en) model for translating classical Sanskrit texts (like Ramayana and Mahabharata) into fluent English.

---

## 📌 Project Highlights

- 🧠 **Base Model**: [`ai4bharat/indictrans2-en`](https://huggingface.co/ai4bharat/indictrans2-en)
- 📚 **Dataset**: [rahular/itihasa](https://huggingface.co/datasets/rahular/itihasa) – ~93k Sanskrit-English shloka pairs
- 🔠 **Input**: Devanagari-script Sanskrit
- 🌐 **Output**: Fluent English translation
- 📊 **Metrics**:
  - BLEU: **37.4**
  - ROUGE-L: **54.6**
  - METEOR: **39.8**

---

## 🔧 Usage (Python)

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

tokenizer = AutoTokenizer.from_pretrained("ayushvjha/Sanskrit-English-Translator")
model = AutoModelForSeq2SeqLM.from_pretrained("ayushvjha/Sanskrit-English-Translator")

input_text = "कौशल्यासुप्रजा राम पूर्वा सन्ध्या प्रवर्तते"
inputs = tokenizer(input_text, return_tensors="pt")
outputs = model.generate(**inputs)
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
