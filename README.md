# Biomedical_Named_Entity_Recognition
Fine-tuning BioBERT for Biomedical Named Entity Recognition on BC5CDR Dataset

The goal of this project was to build a biomedical NER system that can accurately identify chemical and disease entities in biomedical text.

Steps:
Loaded the BC5CDR dataset (chemical/disease entities) from HuggingFace.
Processed the data into BIO tagging format for token classification.
Fine-tuned the pretrained BioBERT model using the HuggingFace Trainer on ~500 training examples.
Evaluated performance using standard NER metrics: precision, recall, F1 (via Seqeval).
Built a Gradio web app for interactive NER on user-input biomedical text.

Results:
After training for 10 epochs, the results show strong overall performance, with especially high precision and recall on chemical entities. Disease entities were slightly weaker, likely due to higher variability and ambiguity in naming. The model generalized well after addressing earlier issues like misaligned BIO tags, label confusion, and insufficient training epochs.
Early runs had near-zero performance, but after fixing data alignment and extending training, scores improved dramatically. Most remaining errors came from: confusing similar-looking entities (chemical names vs disease names), breaking multi-word entities into partial matches, and false positives on rare or unseen entities.

Interactive demo:
Examples you can use for trying it out: "The patient was treated with acetaminophen and ibuprofen for fever. Later, amoxicillin was prescribed to treat a bacterial infection." "Recent studies show that patients with hypertension are at higher risk of developing chronic kidney disease." "Clonidine and naloxone were tested for their effects on spontaneously hypertensive rats, showing significant blood pressure reduction." "Warfarin increases the risk of bleeding when combined with aspirin or clopidogrel." "Alpha-methyldopa is used as an antihypertensive agent, especially in cases of preeclampsia." "Treatment with cisplatin caused nephrotoxicity, leading to renal damage and increased creatinine levels." 

Tools:
Dataset: BC5CDR (from HuggingFace masaenger/bc5cdr)
Model: BioBERT (dmis-lab/biobert-base-cased-v1.1)
Libraries:
HuggingFace Transformers (model + Trainer)
Datasets (HuggingFace for loading and processing)
PyTorch (underlying framework)
Seqeval (for precision, recall, F1 metrics)
Gradio (for demo interface)
