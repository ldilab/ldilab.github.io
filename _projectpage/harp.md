---
paper_name: "<span style='font-family: monospace'>HARP</span>: Hesitation-Aware Reframing in Transformer Inference Pass"
authors:
    - name: Romain Storaï
      affiliation: 1
      mail: romsto@snu.ac.kr
      first: true
    - name: Seung-won Hwang
      mail: seungwon@snu.ac.kr
      affiliation: 1
      corresponding: true
affiliations:
    - Computer Science and Engineering, Seoul National University
bibtex: "@misc{storaï2024harphesitationawarereframingtransformer,\n
      title={HARP: Hesitation-Aware Reframing in Transformer Inference Pass}, \n
      author={Romain Storaï and Seung-won Hwang},\n
      year={2024},\n
      eprint={2412.07282},\n
      archivePrefix={arXiv},\n
      primaryClass={cs.CL},\n
      url={https://arxiv.org/abs/2412.07282}, \n
}"
buttons:
    - name: "arXiv"
      icon: "file-pdf-o"
      link: "https://arxiv.org/abs/2412.07282"
    - name: "Code"
      icon: "github"
      link: "https://github.com/romsto/HARP"
---

# TL;DR

Not all tokens are equally complex to predict - some require more computational resources.
HARP modifies Transformer's forward pass to introduce uncertainty-selective extra computation during inference.
By identifying "harder" tokens through hesitation detection, HARP performs additional computation on reframed inputs.
This method improves overall accuracy, requiring no retraining, and compatible with any Transformer model.

# Abstract

This paper aims to improve the performance of large language models by addressing the variable computational demands in inference steps, where some tokens require more computational resources than others. We present HARP, a simple modification to "off-the-shelf" Transformer forward pass. Drawing from hesitation and the framing effect in decision-making, HARP selectively applies additional computation when the model encounters uncertainty during token generation. Our method mimics human cognitive processes by pausing at difficult decision points and reframing inputs for a different perspective. Unlike other approaches, HARP is model-agnostic, training-free, and easy to implement. We thoroughly evaluate our method across various downstream tasks and model sizes, demonstrating performance improvements up to $$+5.16$$%. Notably, HARP achieves these gains while maintaining inference times twice faster than beam search. Simple and yet with significant gains, HARP offers a practical solution for enhancing the performance of Transformer-based language models with minimal computational impact.

# Our Breakthrough?
We made the Transformer think more like humans, introducing flexibility into its rigid architecture.

# How does it work?
By modifying the transformer forward pass to incorporate:
- **Hesitation** - We detect when the model is uncertain using shannon entropy on logits.
- **Reframing** - When the model hesitates, we reframe the inputs (by applying drop out to the embeddings) and perform an additional forward pass.

![HARP Overview]({{ site.baseurl }}/assets/projects/harp/method_figure.png)  
<div style="text-align: center">
  <em>
    <strong>An overview of the standard vs. HARP-modified Transformer forward pass. HARP detects hesitation and leverages dropout-based perturbation to improve token accuracy.</strong>
  </em>
</div>

# Results

HARP consistently delivers higher performance across models and tasks, with notable gains:
- **LAMBADA**: **+5.16%** accuracy gains (LLaMA 3.1 8B Instruct)
- **GSM8K**: **+4.79%** accuracy gains (Mistral v0.3 8B Instruct)

All of those gains are achieved with a minimal impact:
- only **x1.25** average inference time compared to the base model.
- **twice** faster than beam search.

![Comparison of Accuracy gains and Relative Inference Time for LLaMA 3.1 8B Instruct.]({{ site.baseurl }}/assets/projects/harp/short_results.png)
<div style="display: flex; align-items: center; justify-content: center; text-align: center;">
  <div style="flex: 1; margin-right: 10px; text-align: center;">
    <em>
      <strong>Left:</strong> Relative Accuracy compared to the vanilla model (higher is better). Rouge 1 score is reported for CNN/DailyMail.
    </em>
  </div>
  <div style="flex: 1; margin-left: 10px; text-align: center;">
    <em>
      <strong>Right:</strong> Relative inference time compared to the vanilla model (lower is better).
    </em>
  </div>
</div>
<div style="text-align: center">
  <em>
    <strong>Comparison of Accuracy Gains and Relative Inference Time Across Tasks of LLaMA 3.1 8B Instruct.</strong>
  </em>
</div>

# Why is it amazing?
HARP is **plug-and-play**, requiring no retraining and compatible to any "off-the-shelf" Transformer-based model!