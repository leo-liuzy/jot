# Python

## Preparing `requirements.txt`

```bash
pip install pipreqs
pipreqs /path/to/project
```

# Slurm

**Check my association**

```jsx
sacctmgr show association -p user=$USER
```

**Check the meta-data about a job**

```bash
sstat -j $SLURM_JOB_ID
```

**Check the usage status of a partition**

```bash
sinfo -p
```

# Bash Note

## To sync two folders

```bash
rsync -azP -e ssh <host>:<host-path>/foo**/** <local-path>/foo**/**
```

“/” is very important, otherwise the result will be `<local-path>/foo/foo` rather than `<local-path>/foo`

## Update ruby

```bash
curl -sSL <https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer> | bash -s stable

```

## Loop through `find` results

```bash
find "$CKPT_DIR" -type d -print0 |  while read -d $'\\0' PEFT_MODEL_DIR
do
	echo $PEFT_MODEL_DIR
done
```

## Can’t `rm` because “Device or resource busy”

```bash
lsof +D .vscode-server | awk '{print $2}' | tail -n +2 | xargs -r kill -9
```

# Huggingface

## Downloading models

```python

import huggingface_hub
huggingface_hub.snapshot_download("codellama/CodeLlama-7b-Python-hf", local_dir="/home/zliu/CodeLlama-7b-Python-hf", local_dir_use_symlinks=False)
```

## Downloading datasets

```bash
cd /path/to/parent/dir
git lfs install --skip-repo
git clone git@hf.co:datasets/<dataset ID>
```

## `pipeline`:

`num_return_sequences > 1` will help increase decoding speed. It has the same effect as have multiple copies of input and setting `num_return_sequences = 1`

# Overleaf

Don’t wrap `multicolumn` with `multirow` --> will get stuck

Annotate code with brackets — using `tikz`

```latex
\\begin{lstlisting}[language=Python]
def test_reverse_false():
    # Test case where reverse flag is set to False
    (*@\\tikzmark{t_start}@*)temperature_readings = np.array([22,23,19,20,21]) 
    (*@\\tikzmark{t_end}@*)reverse = False 
    ...
    (*@\\tikzmark{a_start}@*)
    expected_result = np.array([2, 3, 4, 0, 1])
    (*@\\tikzmark{a_end}@*)
    assert np.array_equal(result, expected_result)
\\end{lstlisting}

% say this is in a cell of a `table` environment 
% then the tikz could be place after `tabular` env
\\begin{tikzpicture}[overlay, remember picture]
  \\draw [decoration={brace, amplitude=0.5em, mirror},decorate, thick, gray]
($(pic cs:t_start) + (-2.8em,1.5ex)$) --  ($(pic cs:t_end) + (-2.8em,-0.5ex)$) 
  node [midway, anchor=west,xshift=-1.8em] {$t_i$};
 \\end{tikzpicture}

 \\begin{tikzpicture}[overlay, remember picture]
  \\draw [decoration={brace, amplitude=0.5em, mirror},decorate, thick, gray]
($(pic cs:a_start) + (-3em,1.5ex)$) --  ($(pic cs:a_end) + (-3em,-0.5ex)$) 
  node [midway, anchor=west,xshift=-1.8em] {$a_i$};
 \\end{tikzpicture}
 
```

## arxiv with `minted` package

[https://tex.stackexchange.com/questions/280590/work-around-for-minted-code-highlighting-in-arxiv#comment1207889_414781](https://tex.stackexchange.com/questions/280590/work-around-for-minted-code-highlighting-in-arxiv#comment1207889_414781)

1. Compile with `\\usepackage[finalizecache,cachedir=.]{minted}`.
2. (Overleaf) Go to `logs and output files` > `other logs and files` and download everything with **pyg**.
3. Change `finalizecache` to `frozencache` and upload the tex+all those pyg files to arXiv.

**Optional**:

[https://tex.stackexchange.com/a/661842](https://tex.stackexchange.com/a/661842)

Took the `minted.sty` files directly from [github.com/gpoore/minted/blob/master/source/minted.sty](https://github.com/gpoore/minted/blob/master/source/minted.sty) and put in the (top-level) directory.

# Prompting

Repo to assure structured output from LLM:

[https://github.com/jxnl/instructor](https://github.com/jxnl/instructor)

# Paper reading legend:

Red: that answer important followup question

Yellow: technical details / definition; assumption

Blue: high level summary / rephrasing about technical details;

Green: high level takeaway / motivation for the paper

Purple: example