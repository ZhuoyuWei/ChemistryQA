## Chemistry Exam Question Answering

In recently years, people are probably overwhelmed by news report about AI beat human beings for many times, and some of them are related to Question Answering (QA). For example, IBM Watson won Jeopardy by answering simple questions but with a broad range of knowledge; a lot of neural based models, e.g. XLNet and RoBERTa, beat human beings' performance on both Machine Reading Comprehension and Conversational QA; Ariso System from AI2 gets an 'Ace' for an eighth-grade science examination and is able to give 80 percent correct answers for 12th-grade science test.

Although AI have made such great achievements on the above QA tasks, it is still hard to tell machines have obtained intelligence as human beings. 
Machine intelligence is more appropriately viewed as a diverse collection of capabilities associated with intelligent behavior rather than a binary pass/fail on a specific task. Especially for a real-world QA task, the collection of capabilities should include a) natural language understanding; b) general inference, reasoning and computing; 3) general and domain-specific knowledge applying. 

### An Example
![GitHub Logo](/images/example.png)

### Statics of Dataset

|Train|Dev|Test|
|------------ | -------------|-------------|
|4500| 496|500|

### Dataset download
You can download this dataset at [here](https://github.com/ZhuoyuWei/ZhuoyuWei.github.io/edit/master/README.md).

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
