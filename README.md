## Chemistry Question Answering

In the real world, there are QA tasks which cannot be solved by end-to-end neural networks and is very difficult to translate the natural language to any kind of formal representation which can be solved. Solving Chemical Calculation Problems is such a QA task. We collect about 5,000 chemical calculation problems from \url{https://socratic.org/chemistry}, which cover more than 200 topic in chemistry. Unlike other QA datasets, we propose to only label the variable asked and conditions from question stem, but do not label the complex solving process. We name the dataset as ChemistryQA. To encourage other researchers to explore various solutions, we keep this task weakly supervised.

### An Example
![GitHub Logo](/images/example.png)

### Statics of Dataset

|Train|Dev|Test|
|------------ | -------------|-------------|
|4500| 496|500|

### Dataset download
You can download this dataset at [here](https://...).

### Learderboard

Method| Accuracy on Dev set
------------ | -------------
BERT-based Sequence-to-sequnce Model | 7.03%
Extractor + DFS Solver| 10.4%

### Function Example:

```python

class Func_Mass2Mole(Func):

    name = "Mass2Mole"
    description = "mole=mass/molar_mass"
    output_type="mole"
    input_sat_maps = [["target", "molar_mass"],["target","mass"]]


    def __init__(self,inputs,outputs=None):
        super(Func_Mass2Mole,self).__init__(inputs,outputs)


    def run_func(self):
        if not self.sat_running():
            return False
        molarMass=self.parameters[0].out_node
        mass=self.parameters[1].out_node
        mole_value=mass.value/molarMass.value
        self.outputs[0].out_node=PU(value=mole_value,unit='mole')
        return True

```



Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
