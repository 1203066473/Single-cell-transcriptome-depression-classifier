# Single-cell-transcriptome-depression-classifier
We finetuned a pretrained model (Geneformer https://www.nature.com/articles/s41586-023-06139-9) to obtain a depression classification model using single-cell transcriptome and used in silico perturbation to identify key genes associated with depression.


1. depression.loom: This dataset was utilized for model training, encompassing single-nucleus transcriptomic data derived from the prefrontal cortex of both healthy individuals and those with major depressive disorder. This dataset obtained from GEO Datasets under the reference series GSE144136.(https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE144136)

2. tokenizing_scRNAseq_data_for_finetuning_MDDmodel.ipynb: Convert single-cell transcriptome data in loom format to the rank value data required for model input

3. depression_classification.ipynb: Fine tune depression classification model based on single-cell transcriptome pre-training model

4. in_silico_perturbation: Based on the above fine-tuned depression classification model, use in silico perturbation method to modify the expression of genes and assess the resulting changes in depression classification to determine whether the gene is the key gene causing depression. 
	in_silico_perturbation_ConMDD_delete.ipynb: we removed the given gene from the rank value encoding in healthy people and quantified the cosine shift from the original to perturbed cell embeddings to simulate whether the inhibition of this gene could lead to a transition of the cellular state from healthy to depressed.
	in_silico_perturbation_ConMDD_overexpress.ipynb: we prioritizedt he given gene at the top of the ranking in healthy people and quantified the cosine shift from the original to perturbed cell embeddings to simulate whether the activation of this gene could lead to a transition of the cellular state from healthy to depressed. 
	in_silico_perturbation_MDDCon_delete.ipynb: we removed the given gene from the rank value encoding in depressed people and quantified the cosine shift from the original to perturbed cell embeddings to simulate whether the inhibition of this gene could lead to a transition of the cellular state from depressed to healthy.
	in_silico_perturbation_MDDCon_overexpress.ipynb: we prioritizedt he given gene at the top of the ranking in depressed people and quantified the cosine shift from the original to perturbed cell embeddings to simulate whether the activation of this gene could lead to a transition of the cellular state from depressed to healthy.
