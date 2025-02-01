---
{"dg-publish":true,"permalink":"/bibliometric-sonification-research/bibliometric-sonification-research/"}
---

#### Steps

|Steps|Description|Status|
|---|---|---|
|[[Bibliometric Sonification Research/Steps/Literature Review\|Literature Review]]||In progress|
|[[Bibliometric Sonification Research/Steps/Dataset Analysis\|Dataset Analysis]]|Analyze dataset|In progress|
|[[Bibliometric Sonification Research/Steps/Mappings\|Mappings]]|Find mappings|Not started|
|[[Bibliometric Sonification Research/Steps/Sonification/Sonification\|Sonification]]|Think about sonic relations, materials, and aesthetic vs usage|Not started|

  
  

Web of Science:

[https://www.webofscience.com/wos](https://www.webofscience.com/wos)

  

- Scopus:

[https://www.scopus.com](https://www.scopus.com/)

- DiVA:

[https://kth.diva-portal.org](https://kth.diva-portal.org/)

- Annual Bibliometric Monitoring:

[https://www.kth.se/abm](https://www.kth.se/abm)

- KTH Research Information:

[https://analysis.sy](https://analysis.sys.kth.se/bibliometrics/app_direct/research_info/)

[s.kth.se/bibliometrics/app_direct/research_info](https://analysis.sys.kth.se/bibliometrics/app_direct/research_info/)

### For web-map of bibliometric data:

**Technical Requirements:**

Learn webaudio or else RNBO could work? Which one sounds better?

https://github.com/grame-cncm/faustwasm

I could use Supercollider for prototyping and then re-creating the synths in Faust, no?

So I should do some sound design in Supercollider, like some sounds I like, with specific interactions (frequency and stuff), and then recreate them in Faust.

**Contextual informations:**

Sonifying data in the context of maps or climate data is not a novel concept. Researchers have previously sonified maps into the audio domain using different strategies [9, 15, 29]. In a recent overview study, Lindborg et al. [22] reviewed 32 projects that used sonification of climate change data, 18 of which also integrated visualization of the same data.

[https://dl.acm.org/doi/10.1145/1182475.1182492](https://dl.acm.org/doi/10.1145/1182475.1182492)

[https://www.tandfonline.com/doi/full/10.3109/17483100903100277](https://www.tandfonline.com/doi/full/10.3109/17483100903100277)

[https://www.tandfonline.com/doi/full/10.1080/13658816.2017.1420192](https://www.tandfonline.com/doi/full/10.1080/13658816.2017.1420192)

[https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2022.1020102/full](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2022.1020102/full)

### Aesthetic:

Which aesthetic could match bibliometric data? What do we associate with it? I think of paper, but we have new associations since most of what we do is digital. So maybe the category of research, associating some qualities of the sounds with how their… We must create a set of rules for the mapping, they need to be visible for the people to understand and then we can think of the aesthetic.

Should it match my aesthetic? Should we create generative practices that shape the sound, in the style of CDP? We need sound manipulations that have to be readable, and the interface should also adapt to this multimodality, else there could be issues. A fully acoustic interface works in a certain way, a fully visual interface works in another, and a multimodal one needs to find balance.

  

The sonification of Bornmmann seems not effective, it sounds naive and the cultural background we put in sound heavily influences our perception of them. A better sonification I think is this one [https://archive.org/details/PlanethesizerWindows](https://archive.org/details/PlanethesizerWindows)

I think that what I should get from Bormmann is only the approach to bibliometric data.

  

I still have to consider the relational music concept as discussed by Harry Lehmann.

[https://journals.openedition.org/communication/418](https://journals.openedition.org/communication/418)

I should focus on the timbral characteristics and how they are perceived about materiality and gesture.

I should also re-approach the archetypes defined by Salvatore Sciarrino in “Le figure della musica”.

[https://www.youtube.com/watch?v=YUYvzAg_INA](https://www.youtube.com/watch?v=YUYvzAg_INA)

[https://vimeo.com/138020286](https://vimeo.com/138020286)

[https://www.youtube.com/watch?v=-_g26h9YJRU](https://www.youtube.com/watch?v=-_g26h9YJRU)

[https://vtol.cc/filter/works/silk](https://vtol.cc/filter/works/silk)

[http://www.francescofabris.com/?project=stellar](http://www.francescofabris.com/?project=stellar)

[http://www.francescofabris.com/?project=stillaeolian](http://www.francescofabris.com/?project=stillaeolian)

fabris quindi fa robe fighe partendo dalle sonificazioni, bene.

quindi diciamo che un’estetica più sonology può funzionare meglio per le sonification, perchè sennò si rischia il new age.

Ora è da vedere se un’estetica più composta può funzionare, il problema è che si presta al minimalismo il tutto, cioè pochi elementi riconoscibili.

  

Ripescare le slides di bjarni per supercollider, il suo stile si adatta bene per un primo progetto di sonification come questo.

  

### Mapping:

Which information is most relevant? The impact? The connections? How do we render the connections? I think there could be different levels of representation and artistic outcomes. A practical one (reading the data), an interactive one (interacting for awareness, installations), and a creative one (displaying how this data shapes research and funding).

**Example:**

For example, a lack of pollution could sound harmonious and beautiful, while more pollution could sound distressing, dissonant, and unpleasant.

> [!important] Ok fine, but isn’t this a simplistic view? Perception is more complicated, cultural environment and musical background change drastically how someone perceives sound. Something harmonious for one, may sound boring to others causing attention to lack.
> 
> What instead could be useful would be to get these ideas from nature or extra-musical material that can be recognized in a more primordial meaning. Going after the archetypes, not the _not-so-_constantly evolving Western musical tradition.
> 
> Anyway portraying negativity with sound is difficult as a composer, like to some it may result negative but to others it may signify something else. Like as Leigh Landy in “Understanding The Art of Sound Organization” marks with Ligeti and Kubrick, the use of K. of L.’s music is out of context in respect to the composer’s idea.
> 
> I mean perception studies like the ones of Huron.

Like we have this article and many more: [https://www.nature.com/articles/nature.2012.11791](https://www.nature.com/articles/nature.2012.11791)

But my issue is how diverse was the test group? Did they only come from western cultures? Is the cultural egemony of western media so strong that cultures where the dissonance is musically perceived differently adapted to our musical preferences? Isn’t this sort of a post-colonialism issue?

Again this review, published by Harvard seems to be full of bullshit: [https://ui.adsabs.harvard.edu/abs/2023PhLRv..46...69P/abstract](https://ui.adsabs.harvard.edu/abs/2023PhLRv..46...69P/abstract)

This method: _“To generate dissonant music the authors selected 10 happy and major mode excerpts from Verdi's "La Traviata" opera (transcribed for piano), and modified them by shifting the pitch of the tones of the leading voice by one semitone (either upward or downward), leading to 20 dissonant versions”._

Of course it’s unpleasing because it wasn’t composed to be like that! If used in a creative context we may have a “dissonant” cluster which maybe could invoke a relaxation on the listener, maybe we have a fast paced articulation and then there’s a long drone, which could have some dissonant components. How do we see it then?

  

We have tension and release in music. It’s not only consonance and dissonance. If we shift our perspective to sound spectra or tunings different from equal tempered, we will see how these issues manifest themselves.

  

Take for example a bell sound, it is inharmonic but at the same time it is seen often as a cultural object that represent spirituality, calmness.

  

So dissonant timbre is not problematic? dissonant chords are?

  

This should be studied thoroughly.

  

It really depends on the listening conduct

We should listen at sound for sound itself, that way we can have take a step back at the cultural background and really infuse informations in something.

  

[http://sonify.psych.gatech.edu/research/aquarium/index.html](http://sonify.psych.gatech.edu/research/aquarium/index.html)

For this one i have mixed feelings: it sounds bad, but one of the examples actually worked for me to understand the movement of the ants. The canon one instead was too complicated, it seemed almost detached from the information inside the video.

  

Somax 2 should also be considered, as it is partially generative.

  

Dictionary based sonification? Concatenative Synthesis? Generate first a dictionary of variation of an original material and map it for sonification?

  

  

  

Graphical Notation and the interpretation of it by musicians: Sylvano Bussotti, Jani Christou, the other one i always forget the name.

Huge issue of sonification: lots of papers, not a unified platform to listen to them and evaluate their results. It’s a sonic experiment, I must listen to it.

  

  

  

![image 4.png|image 4.png](/img/user/Assets/image%204.png)