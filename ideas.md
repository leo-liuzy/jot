## Knowledge representation

Philosophical standpoint: reasoning is a sprinkle on top of a perfect knowledge representation
* Though I know little about the subject...
Why does the old way to go about knowledge representation fail?

Could we improve the quality of KR through interaction with the environment? Like CLIN?

Could we view the learning through the lens of “a better KR helping model better reason”?  

## Knowledge conflict

In a continual learning setup, what are the types of knowledge that a model better remembers in its parametric knowledge and what are the ones that should/could be out-sourced to RAG / other models? 
* What would be a good setting to study this? Should I figure this out?

## Knowledge updating
Premise: since continual learning and forgetting is a contradictory desiderata, why don’t we intentionally forget things and make room for continually learning knowledge?

### Intentional forgetting
Before a model forgets things, can we somehow “distill” the knowledge from the model into an adapter; and then store the adapter somewhere in case in the future we need to plug this knowledge back into the model; then. the model goes ahead intentionally forgetting or overwriting this knowledge to inject or update new knowledge.


Two gold paragraphs are in the same context. Does this cause the big increase in multi-hop question?
* Train on individual paragraphs
If it does impact the MHQ, could we compare gradient from training on individual paragraphs vs training on two parapgraph concat, and learn an oracle network that learn to obtain that "propagation direction". This is also to do a feasible test under an idea situation.

## Brainstorming: Diffusion model as hypernetwork

Any concerns down this road?

https://arxiv.org/abs/2402.13144



## Build consistent belief of LLM through interactive learning / interventional learning
CLIN + Belief of LLM
Build belief net from LLM before any interaction about the world; then, have the agent to interact and update the belief net; let the model either condition its behavior on the belief net; or see a way to burn the world model into the LM, so that the LLM could have a consistent belief. 


## Multimodal propagation
Continual learning should be multimodal, and, more interestingly, different modalities should go hand in hand.

e.g. letting the model to see new DJT's new official president image; then prompt the model to describe the image. See if the model would give the new description rather than the description about the old image.