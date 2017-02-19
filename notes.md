## 170219

I've been trying to get sonnetizer to run again. For me, that means learning more about Python and NLTK by poking around at existing code and development threads. As of this afternoon I think that I'm stuck because the original `NgramModel()` that @rossgoodwin used has been deprecated at NLTK and rebuilt from the ground up, mostly by Ilia Kurenkov (@Copper-Head). I've figured out (I think) how to implement the ngram models -- at least the MLENgramModel -- but [the old attribute  `.generate`](http://www.nltk.org/_modules/nltk/model/ngram.html#NgramModel.generate) that @rossgoodwin uses to create the lines in sonnetizer is no longer supported. 

### Updates/changes I've been able to make given my limited acumen:  
*  imported codecs and revised the `open()` function call to fix ascii interpreter problems.  
*  imported the proper libraries from nltk.model: `build_vocabulary, count_ngrams, MLENgramModel`  
*  commented the daylights out of what I could understand. Once @rossgoodwin starts building his rhyming and lineation algorithms I'm pretty out of my depth, but I trust that they'd work if I could just get a module that random text based on the language model.  
*  added printout counts of valid words and unique words, for grins.
*  gotten the model (`MLENgramModel`) to not throw an error until it tries to call `.generate`. 

### Annotated list or resources that has gotten me this far in my quest to bring Sonnetizer back to life.
* Issue [#738](https://github.com/nltk/nltk/issues/738) // Demonstrates the breadth of the timeline here: it starts in AUG 2014 and includes comments from users a few weeks ago (JAN 2017).  
* Issue [#937](https://github.com/nltk/nltk/pull/937) // This is good for context only, at least for me. It's a little inside baseball about stress tests, but helps shape the development timeline from APR 2015, and then a year later points to more recent developments.  
*  Issue [#1342](https://github.com/nltk/nltk/issues/1342) // From MAR 2016, helps to contextualize the redevelopment of the model. And from OCT 2016 shows where development stands.  
*  [This from StackOverflow](http://stackoverflow.com/questions/37504391/train-ngrammodel-in-python) and [these doctests](https://github.com/nltk/nltk/blob/model/nltk/test/model.doctest) are from last summer (2016) and were really helpful as I tried to update the Sonnetizer code to get the smoothing algorithms to run. I'm still not entirely sure if I have them running well yet, but I'm at leat closer.  
*  Not related to the development of the ngram models, but [this from stackoverflow](http://stackoverflow.com/questions/28501072/how-to-check-which-version-of-nltk-scikit-learn-installed) helps me remmeber how to see which NLTK I'm running. (3.2.1 right now, because "model" isn't in 3.2.2).  

### Next Actions
My next steps will be to reach out to someone who might be able to help me determine if I'm interpreting all of this correctly and maybe point me toward some resources for getting generating text based on the language model. In a real revision I'll want to update the codebase from Python 2.7 to 3.x as well. 
