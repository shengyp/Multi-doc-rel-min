## Coherence and Salience-Based Multi-Document Relationship Mining

We propose a unified framework to aid users in quickly discerning salient connections and facts from a set of related documents, and presents the resulting information in a graph-based visualization.

### The Framework of Our Approach

![](figs/model.png)

In summary, this framework can be best described as a combination of three major subtasks:

1.  **Candidate Facts Extraction**
    

-   **Document Ranking**
    
-   **Coreference Resolution**
    
-   **Sentence Ranking**
    
-   **Candidate Relational Triples Extraction**
    

To illustrate this, we shall consider an example sentence is ”George .” Such a sentence yields a number of triples, among which we may find (The United States, President, Trump), (noun phrase, relation phrase, noun phrase), (noun phrase, relationphrase, noun phrase).

**2. Topic Coherence Estimation of Candidate Facts**

-   In\_Titles, the frequency of candidates in document titles is divided into three cases: greater than 13.40, less than 3.16, and between 3.16 and 13.40. Three binary features are used to represent these cases.
    
-   Compatibility, the compatibility between the $relation\_context$ of the relation $r$ in the candidate triple $f$ and the semantic information of $f$ itself, i.e.,
    

$$
Cmp(r_{f}, f_{ht}) = RelCxt(r_{f}, l) \cdot (1 - \epsilon + \epsilon \cdot Sem(f_{ht}, context(r_{f})))
$$

Here, the first term $RelCxt(r_{f}, l)$ denotes the $relation\_context$ of $r$ in $f$ as computed in Equation 2; the second term denotes the ratio of the number of candidates that have same \emph{subject} $s$ or \emph{object} $o$ with $f$ from $RelCxt(r_{f}, l)$, which is calculated by $Sem(r_{f}, f_{ht}) = \frac{count_{f_{ht}}}{count_{context(r_{f})}}$. Parameter $\epsilon$ is used for smoothing as well as to control the influence of the \emph{relation context}, and is fixed to 0.5 in our implementation.

**3. Conceptual Graph Construction**

The reached data from prior fact extraction module can be filtered such that only the most salient, confident, and compatible facts are maintained. That is, fact filtering module aims at hiding less representative facts in the visualization and the filtered results can be retrieved from [here](https://github.com/shengyp/Multi-Docs-semantics/blob/master/data/elections/filtering-facts).

$$
I_{i}= (1 - d)\sum_{j \in N(i)}\frac{w_{ji}}{\Sigma_{k\in N(j)}w_{jk}}I(j) + d \cdot p_{i},
$$

where $N(i)$ stands for the set of the node $v_{i}$'s neighbors.

### Dataset

The reached data from prior fact extraction module can be filtered such that only the most salient, confident, and compatible facts are maintained. That is, fact filtering module aims at hiding less representative facts in the visualization and the filtered results can be retrieved from [here](https://github.com/shengyp/Multi-Docs-semantics/blob/master/data/elections/filtering-facts).

### Experiments

Exp.

### Code Repository

The code used in this paper will be updated after the work be accepted.

```markdown
Syntax highlighted code block

# Header 1

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/shengyp/Multi-doc-rel-min/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.
