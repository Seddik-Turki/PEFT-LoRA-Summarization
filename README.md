# PEFT-LoRA-Summarization
## Description
This project implements a dialogue summarization model using Parameter Efficient Fine-Tuning (PEFT) with `LoRA` on the `FLAN-T5` architecture.</br>
This project compares `LoRA` with traditional fine-tuning methods to evaluate efficiency and performance, key comparison include <code>Training Time</code>,`ROUGE` score and `N° of trainable parameters`.

## Examples
**Original Dialogue**

```python
#Person1#: Have you considered upgrading your system?
#Person2#: Yes, but I'm not sure what exactly I would need.
#Person1#: You could consider adding a painting program to your software.
           It would allow you to make up your own flyers and banners for advertising.
#Person2#: That would be a definite bonus.
#Person1#: You might also want to upgrade your hardware because it is pretty outdated now.
#Person2#: How can we do that?
#Person1#: You'd probably need a faster processor, to begin with. And you also need a more powerful hard disc,
           more memory and a faster modem. Do you have a CD-ROM drive?
#Person2#: No.
#Person1#: Then you might want to add a CD-ROM drive too, because most new software programs are coming out on Cds.
#Person2#: That sounds great. Thanks.
```
**Summaries**


```python
---------------------------------------------------------------------------------------------------
BASELINE HUMAN SUMMARY:
#Person1# teaches #Person2# how to upgrade software and hardware in #Person2#'s system.
---------------------------------------------------------------------------------------------------
ORIGINAL MODEL:
#Person1# suggests upgrading #Person2#'s system to make up some flyers and banners.
#Person2# also suggests upgrading #Person1#'s hardware.
---------------------------------------------------------------------------------------------------
INSTRUCT MODEL:
You might want to upgrade your computer.
---------------------------------------------------------------------------------------------------
PEFT MODEL:
#Person2# wants to upgrade #Person2#'s system and hardware. #Person1# recommends adding a painting
program to #Person2#'s software and adding a CD-ROM drive.
---------------------------------------------------------------------------------------------------
```
</br>

## Project Structure
In this project the FLAN-T5 model was finetuned on the [dialogsum](https://huggingface.co/datasets/knkarthick/dialogsum). All the code for the project can be found in the `PEFT LoRA-Enhanced Dialogue Summarization.ipynb` Notebook. Here's an overview of the code:
  * **Data & model Preparation**:
  * **Zero-shot Inference**:
  * **Full Fine-Tuning**: 
  * **PEFT Fine-Tuning**: Configure parameters such as the rank `r = 32` and the target modules `q` and `v`.
  * **Evaluation**:Two main appraoches for evaluation:
      * **Qualitative (Human-Based) Evaluation**: 
      * **Quantitative Evaluation with ROUGE metrics**:

## Results
### N° of parameters
| Model           | Trainable Parameters | All Parameters | Percentage of Trainable Parameters |
|-----------------|----------------------|----------------|------------------------------------|
| Original Model  | 247,577,856          | 247,577,856    | 100%                               |
| PEFT Model      | 3,538,944            | 251,116,800    | 1.41%                              |

</br>

### Training Time
| Model           | Training Time (mn) |
|-----------------|---------------|
| Original Model  | 38:20         |
| PEFT Model      | 31:20         |

</br>

### ROUGE Scores
| Model           | ROUGE-1 | ROUGE-2 | ROUGE-L | ROUGE-Lsum |
|-----------------|---------|---------|---------|------------|
| Original Model  | 0.2001  | 0.0583  | 0.1724  | 0.1726     |
| Instruct Model  | 0.2228  | 0.0766  | 0.1938  | 0.1943     |
| PEFT Model      | 0.4037  | 0.1549  | 0.3216  | 0.3219     |





