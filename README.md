# Word2Vec Project

In this project, you will create a simple search engine for the website <https://www.lawfareblog.com>.
This website provides legal analysis on US national security issues.

**Due date:** Sunday, 11 December at midnight

**References:**

Word2Vec high-level overview: <https://blog.acolyer.org/2016/04/21/the-amazing-power-of-word-vectors/>

Word2Vec details with math: <http://arxiv.org/abs/1402.3722v1>

Interesting applications:

1. machine translation with word2vec: <https://arxiv.org/abs/1309.4168>

1. measuring gender bias in text corpora: <http://wordbias.umiacs.umd.edu/>

1. measuring racial bias in text corpora: <https://www.pnas.org/content/115/16/E3635/tab-figures-data>

1. measuring semantic shift in word meaning: <https://nlp.stanford.edu/projects/histwords>

## Task 1: finding similar words

Recall that we can use the `pagerank.py` file to find the "highest quality" search results from the <https://lawfareblog.com> website.

For example, searching for "weapons" gives us:
```
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='weapons'
INFO:root:rank=0 pagerank=0.0011619674041867256 url=www.lawfareblog.com/slaughterbots-and-other-anticipated-autonomous-weapons-problems
INFO:root:rank=1 pagerank=0.0006675782497040927 url=www.lawfareblog.com/history-do-it-yourself-weapons-and-explosives-manuals-america
INFO:root:rank=2 pagerank=0.0006599930347874761 url=www.lawfareblog.com/lethal-autonomous-weapons-systems-first-and-second-un-gge-meetings
INFO:root:rank=3 pagerank=0.0006531275575980544 url=www.lawfareblog.com/lethal-autonomous-weapons-systems-recent-developments
INFO:root:rank=4 pagerank=0.0006407579057849944 url=www.lawfareblog.com/too-early-ban-us-and-uk-positions-lethal-autonomous-weapons-systems
INFO:root:rank=5 pagerank=0.0006338492385111749 url=www.lawfareblog.com/living-weapons-biological-warfare-and-international-security-gregory-koblentz
INFO:root:rank=6 pagerank=0.0005889176391065121 url=www.lawfareblog.com/critical-gaps-remain-defense-department-weapons-system-cybersecurity
INFO:root:rank=7 pagerank=0.0005780397332273424 url=www.lawfareblog.com/digital-strangelove-cyber-dangers-nuclear-weapons
INFO:root:rank=8 pagerank=0.0005346386460587382 url=www.lawfareblog.com/chemical-weapons-syria-enough-justify-use-force
INFO:root:rank=9 pagerank=0.0005290458793751895 url=www.lawfareblog.com/complexities-usg-covert-action-supply-weapons-syrian-rebels
```
and searching for "drones" gives us:
```
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='drones'
INFO:root:rank=0 pagerank=0.0006651429575867951 url=www.lawfareblog.com/future-violence-robots-and-germs-hackers-and-drones-confronting-new-age-threat
INFO:root:rank=1 pagerank=0.000632093520835042 url=www.lawfareblog.com/faa-wants-hear-you-about-privacy-and-domestic-drones
INFO:root:rank=2 pagerank=0.0006249933503568172 url=www.lawfareblog.com/ryan-calo-faas-setback-domestic-drones
INFO:root:rank=3 pagerank=0.0005648414953611791 url=www.lawfareblog.com/future-violence-now-hostile-use-drones
INFO:root:rank=4 pagerank=0.0005380361108109355 url=www.lawfareblog.com/lawfare-podcast-episode-5-missy-cummings-drones-drones-drones
INFO:root:rank=5 pagerank=0.0005302542704157531 url=www.lawfareblog.com/transcript-john-brennans-speech-yemen-and-drones
INFO:root:rank=6 pagerank=0.0005287894746288657 url=www.lawfareblog.com/no-more-drones-cia
INFO:root:rank=7 pagerank=0.0005287464591674507 url=www.lawfareblog.com/defending-drones-oxford-union
INFO:root:rank=8 pagerank=0.0005245042848400772 url=www.lawfareblog.com/readings-civilian-intelligence-agencies-and-use-armed-drones-ian-henderson
INFO:root:rank=9 pagerank=0.0005204146727919579 url=www.lawfareblog.com/wittes-v-oconnell-targeted-killing-and-drones
```
and searching for "targets" gives us:
```
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='targets'
INFO:root:rank=0 pagerank=0.0005385450785979629 url=www.lawfareblog.com/exclusive-nsa-program-can-target-thoughts-millions-targets-thousands-americans
INFO:root:rank=1 pagerank=0.0005327311810106039 url=www.lawfareblog.com/saudi-women-granted-new-rights-kurdistan-under-pressure-after-referendum-egypt-targets-dissidents
INFO:root:rank=2 pagerank=0.0005264155333861709 url=www.lawfareblog.com/turkeys-referendum-pushes-country-toward-authoritarianism-attack-targets-civilians-syrian-ceasefire
INFO:root:rank=3 pagerank=0.0005200763698667288 url=www.lawfareblog.com/british-anwar-al-awlaki-scenario-uk-targets-british-isil-member-syria-imminentcontinuous-threat
INFO:root:rank=4 pagerank=0.0005126169417053461 url=www.lawfareblog.com/middle-east-ticker-mosul-offensive-begins-us-fires-targets-yemen-and-what-intervention-syria-will
INFO:root:rank=5 pagerank=0.0005046890000812709 url=www.lawfareblog.com/us-forces-said-have-bombed-isis-targets-iraq
INFO:root:rank=6 pagerank=0.0005030750180594623 url=www.lawfareblog.com/trumps-big-middle-east-trip-us-targets-assad-forces-syria-and-iran-goes-polls
INFO:root:rank=7 pagerank=0.0005025876453146338 url=www.lawfareblog.com/international-fallout-trumps-immigration-and-refugee-order-us-raid-targets-aqap-yemen-greece-turkey
INFO:root:rank=8 pagerank=0.0005012631299905479 url=www.lawfareblog.com/der-spiegel-claims-germany-witholds-intel-militants-who-might-be-drone-strike-targets
INFO:root:rank=9 pagerank=0.0005012631299905479 url=www.lawfareblog.com/what-right-number-call-detail-records-42-targets-under-fisas-business-records-authority
```

Notice that the results for each of these terms do not overlap at all.

In a real search engine, however, we probably want to return results that mention "drones" or "targets" if someone searches for "weapons" since these terms are highly related.
Word vectors give us a tool for doing this.

In particular, we can use the [gensim](https://radimrehurek.com/gensim/) python library and pretrained word vectors to find words similar to the search word, and search for those as well.
For example, we can find words related to "weapons" by running the python code
```
>>> import gensim.downloader
>>> vectors = gensim.downloader.load('glove-twitter-25')
>>> vectors.most_similar('weapons')
[('drones', 0.8980589509010315),
 ('drone', 0.8965809345245361),
 ('assault', 0.8937929272651672),
 ('targets', 0.8834593296051025),
 ('firearms', 0.8833326697349548),
 ('weapon', 0.8730441927909851),
 ('hiv', 0.8625047206878662),
 ('laws', 0.8613511323928833),
 ('drug', 0.8555657863616943),
 ('concealed', 0.8548306822776794)
]
```
Notice that both the words "drones" and "targets" appear in this list of similar words.
The list isn't perfect though... "hiv" doesn't seem very similar to "weapons" to me.

Part of the problem is that I'm using a particularly poor model above that has a relatively large out-of-sample error.
The `glove-twitter-25` model is trained only on twitter data and has only 25 dimensions.
We've seen from our discussion about statistical learning theory that:

1. Increasing the number of training data points will improve generalization error, but won't improve training error.

1. Increasing the number of dimensions will improve training error but hurt generalization error.

In practice, there is lots of data available for training word embeddings in English.
State-of-the-art word embeddings are trained on multi-petabyte datasets of webpage crawls,
and so they can have a very high dimension and still achieve low generalization error.
For rarer languages, however, less training data is available,
and so models with fewer dimensions are more effective.

For this assignment, you won't have to train your own model from scratch,
and can instead use a pretrained model.
You must select a model different from `glove-twitter-25`, since that's a particularly bad one.
You won't be evaluated on how good of a model you select,
but I encourage you to spend some time experimenting with different models to see what works well for this application.
You can find a list of models built into gensim [here](https://github.com/RaRe-Technologies/gensim-data#models),
and there's many other open source models that people have released.

**Your Task:**

Modify the `pagerank.py` file so that it also searches for the keywords in the query and the 5 most similar words.
The results of your modified file when searching for "weapons" should look something like:
```
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='weapons'
INFO:root:rank=0 pagerank=0.004571518860757351 url=www.lawfareblog.com/why-did-you-wait-moral-emptiness-and-drone-strikes
INFO:root:rank=1 pagerank=0.0031107424292713404 url=www.lawfareblog.com/dc-district-court-dismisses-journalists-drone-lawsuit
INFO:root:rank=2 pagerank=0.0020231129601597786 url=www.lawfareblog.com/revived-cia-drone-strike-program-comments-new-policy
INFO:root:rank=3 pagerank=0.0019667143933475018 url=www.lawfareblog.com/us-court-appeals-dc-circuit-dismisses-suit-over-us-drone-strike
INFO:root:rank=4 pagerank=0.001178761012852192 url=www.lawfareblog.com/iran-shoots-down-us-drone-domestic-and-international-legal-implications
INFO:root:rank=5 pagerank=0.0011619674041867256 url=www.lawfareblog.com/slaughterbots-and-other-anticipated-autonomous-weapons-problems
INFO:root:rank=6 pagerank=0.0011276121949777007 url=www.lawfareblog.com/german-courts-weigh-legal-responsibility-us-drone-strikes
INFO:root:rank=7 pagerank=0.0008373793680220842 url=www.lawfareblog.com/shift-jsoc-drone-strikes-does-not-mean-cia-has-been-sidelined
INFO:root:rank=8 pagerank=0.0007856971933506429 url=www.lawfareblog.com/waiving-imminent-threat-test-cia-drone-strikes-pakistan
INFO:root:rank=9 pagerank=0.0007412837585434318 url=www.lawfareblog.com/drone-strike-errors-and-hostage-tragedy-mapping-issues-newly-catalyzed-debate
```

Notice that most of these articles do not mention the word "weapons",
but instead mention the word "drone".

> *NOTE:*
>
> Your numbers and order of results will likely be slightly different.
> That's okay as long as they're reasonable.
> For example, you should be returning some results that do not contain the search word,
> but contain related words.

> *HINT:*
>
> The easiest way to implement this task is to modify the `url_satisfies_query` function so that it calls gensim's `most_similar` function on each of the input query words,
> and returns `True` if any of those words are in the list.
> I recommend using only the 5 most similar words,
> as the words quickly become fairly unrelated.

## Task 2: ranking with word importance

There are several problems with the method above for including similar words in our search results.
For example:

1. Some words have lots of very similar words.
   Consider the most similar words for the search "biden":
   ```
   >>> vectors.most_similar('biden')
   [('hillary', 0.9419968128204346),
    ('christie', 0.9419272541999817), 
    ('romney', 0.9377604722976685), 
    ('potus', 0.9371991157531738), 
    ('reid', 0.9328151345252991), 
    ('boehner', 0.9311597347259521), 
    ('clinton', 0.9253027439117432), 
    ('clegg', 0.9072402119636536), 
    ('miliband', 0.9010352492332458), 
    ('zimmerman', 0.8950174450874329)
    ]
   ```
   All of the results above are more similar to "biden" than any word is to "weapons".
   So if we are only looking at the top5 words for everything,
   then some words will get much better matches than others.
   It would be better to have an adaptive method that can automatically determine the top number of query results to use.

1. If someone is searching for "weapons",
   we should probably weight articles about weapons higher than articles about "drones",
   and we should rank articles about both "drones" and "weapons" the highest.
   Our previous method ranks all of these results equally.

One simple method for fixing both of these problems to define a `query_score` for each webpage in addition to the pagerank score `pi`.
This `query_score` would be a real number that depends on both the query and the article's text,
and would be high whenever the query and text are related to each other.
Then the webpage's ranking would be defined by:
```
ranking = pi * query_score
```
Instead of only by the pagerank `pi`.

There are many possible ways to define the query score.
For example, if we define the `query_score` to be 0 when `url_satisfies_query` returns `False` and 1 when it returns `True`,
then this algorithm reduces to the previous algorithm.

A better method is to use the similarity scores using the following pseudocode:
```
score = 0
let S be the set of words similar to the query string
for each word in S:
    let n be the number of times word appears in document
    let word_similarity be the similarity score of word
    score += n * word_similarity**p
```
By adjusting the p hyperparameter, we can control how important the word similarities must be.
A typical `p` value would be between 30-60, since this will result in scores roughly on a similar scale as the pagerank vectors.
You should hard-code this value to something that you think gives reasonable results.

> *NOTE:*
> 
> The optimal value for `p` will depend on the particular word embeddings you select.
> In real world search engines, the optimal value would be learned from the data.
> We would set up a classification problem where the output variable `Y` to be predicted is whether or not a user clicks on one of the links provided,
> and the input variable `X` would be the search term.
> The hypothesis class would be the pseudo-code you've written above with `p` as the only parameter to be learned.
> Then you can use gradient descent to solve for `p`.
>
> You won't have to do this.
> It is hard to implement because this is a non-standard hypothesis class not found in libraries scikit-learn,
> and acquiring reasonable training data is difficult for companies not already operating large-scale search engines.
>
> Google uses classification problems like this internally all over their search engine.
> When Google was first founded, it was common to hear people saying "Google uses machine learning the way Microsoft uses the if statement."
> Now all the major tech companies have machine learning problems like this internally that they are solving,
> so people don't say this anymore.

**Task:**

Implement the "better method" described above.
You will have to modify the `WebGraph.search` function so that it implements the pseudocode described above,
and orders documents according to the `ranking` score instead of according to `pi`.

## Submission

1. Create a new repo on github (not a fork of this repo).

1. Run the following commands, and paste their output into the code blocks below.

   Task 1, part 1:
   ```
   $ python3 pagerank.py --data=small.csv.gz --verbose
   DEBUG:root:computing indices
   DEBUG:root:computing values
   DEBUG:root:i=0 residual=0.3775096535682678
   DEBUG:root:i=1 residual=0.3134882152080536
   DEBUG:root:i=2 residual=0.27565914392471313
   DEBUG:root:i=3 residual=0.21698100864887238
   DEBUG:root:i=4 residual=0.18984201550483704
   DEBUG:root:i=5 residual=0.15531453490257263
   DEBUG:root:i=6 residual=0.13266243040561676
   DEBUG:root:i=7 residual=0.11062289774417877
   DEBUG:root:i=8 residual=0.0935135930776596
   DEBUG:root:i=9 residual=0.07847178727388382
   DEBUG:root:i=10 residual=0.06611073762178421
   DEBUG:root:i=11 residual=0.05558084324002266
   DEBUG:root:i=12 residual=0.04677915573120117
   DEBUG:root:i=13 residual=0.03934914246201515
   DEBUG:root:i=14 residual=0.033108580857515335
   DEBUG:root:i=15 residual=0.027854058891534805
   DEBUG:root:i=16 residual=0.023434894159436226
   DEBUG:root:i=17 residual=0.01971624046564102
   DEBUG:root:i=18 residual=0.016587793827056885
   DEBUG:root:i=19 residual=0.01395573653280735
   DEBUG:root:i=20 residual=0.01174134574830532
   DEBUG:root:i=21 residual=0.009878423996269703
   DEBUG:root:i=22 residual=0.008310978300869465
   DEBUG:root:i=23 residual=0.00699202623218298
   DEBUG:root:i=24 residual=0.005882850848138332
   DEBUG:root:i=25 residual=0.004949328955262899
   DEBUG:root:i=26 residual=0.004163879435509443
   DEBUG:root:i=27 residual=0.0035032741725444794
   DEBUG:root:i=28 residual=0.002947525354102254
   DEBUG:root:i=29 residual=0.002479689661413431
   DEBUG:root:i=30 residual=0.0020862016826868057
   DEBUG:root:i=31 residual=0.0017553460784256458
   DEBUG:root:i=32 residual=0.0014767615357413888
   DEBUG:root:i=33 residual=0.0012426351895555854
   DEBUG:root:i=34 residual=0.0010450585978105664
   DEBUG:root:i=35 residual=0.0008793887100182474
   DEBUG:root:i=36 residual=0.0007399079040624201
   DEBUG:root:i=37 residual=0.0006227020639926195
   DEBUG:root:i=38 residual=0.0005236920551396906
   DEBUG:root:i=39 residual=0.0004406478547025472
   DEBUG:root:i=40 residual=0.000370639783795923
   DEBUG:root:i=41 residual=0.0003121042682323605
   DEBUG:root:i=42 residual=0.00026231163064949214
   DEBUG:root:i=43 residual=0.0002206446515629068
   DEBUG:root:i=44 residual=0.00018575278227217495
   DEBUG:root:i=45 residual=0.00015623871877323836
   DEBUG:root:i=46 residual=0.00013146748824510723
   DEBUG:root:i=47 residual=0.00011045498831663281
   DEBUG:root:i=48 residual=9.31432587094605e-05
   DEBUG:root:i=49 residual=7.8285884228535e-05
   DEBUG:root:i=50 residual=6.595712329726666e-05
   DEBUG:root:i=51 residual=5.543767110793851e-05
   DEBUG:root:i=52 residual=4.662797800847329e-05
   DEBUG:root:i=53 residual=3.916498098988086e-05
   DEBUG:root:i=54 residual=3.3166303182952106e-05
   DEBUG:root:i=55 residual=2.767469413811341e-05
   DEBUG:root:i=56 residual=2.3180422431323677e-05
   DEBUG:root:i=57 residual=1.9749610146391205e-05
   DEBUG:root:i=58 residual=1.6450476323370822e-05
   DEBUG:root:i=59 residual=1.3971823136671446e-05
   DEBUG:root:i=60 residual=1.1601221558521502e-05
   DEBUG:root:i=61 residual=9.941520147549454e-06
   DEBUG:root:i=62 residual=8.237256224674638e-06
   DEBUG:root:i=63 residual=7.062458735163091e-06
   DEBUG:root:i=64 residual=5.890389729756862e-06
   DEBUG:root:i=65 residual=4.963853825756814e-06
   DEBUG:root:i=66 residual=3.989728611486498e-06
   DEBUG:root:i=67 residual=3.7243364658934297e-06
   DEBUG:root:i=68 residual=2.826982381520793e-06
   DEBUG:root:i=69 residual=2.5576227926649153e-06
   DEBUG:root:i=70 residual=2.092539034492802e-06
   DEBUG:root:i=71 residual=1.8848643321689451e-06
   DEBUG:root:i=72 residual=1.5724784816484316e-06
   DEBUG:root:i=73 residual=1.118282284551242e-06
   DEBUG:root:i=74 residual=1.1496127854115912e-06
   DEBUG:root:i=75 residual=8.259061701210157e-07
   INFO:root:rank=0 pagerank=2.1634e+00 url=4
   INFO:root:rank=1 pagerank=1.6664e+00 url=6
   INFO:root:rank=2 pagerank=1.2402e+00 url=5
   INFO:root:rank=3 pagerank=4.5712e-01 url=2
   INFO:root:rank=4 pagerank=3.5620e-01 url=3
   INFO:root:rank=5 pagerank=3.2078e-01 url=1
   ```

   Task 1, part 2:
   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --search_query='corona'
   INFO:root:rank=0 ranking=1.7760e-11 url=www.lawfareblog.com/ted-cruz-vs-section-230-misrepresenting-communications-decency-act
   INFO:root:rank=1 ranking=1.7104e-11 url=www.lawfareblog.com/guess-what-play-ted-cruz-read-filibuster
   INFO:root:rank=2 ranking=1.7055e-11 url=www.lawfareblog.com/publicity-stunt-postscript-senators-cruz-and-paul-propose-legislation-targeted-killing-domestic
   INFO:root:rank=3 ranking=0.0000e+00 url=www.lawfareblog.com/lawfare-podcast-united-nations-and-coronavirus-crisis
   INFO:root:rank=4 ranking=0.0000e+00 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
   INFO:root:rank=5 ranking=0.0000e+00 url=www.lawfareblog.com/britains-coronavirus-response
   INFO:root:rank=6 ranking=0.0000e+00 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
   INFO:root:rank=7 ranking=0.0000e+00 url=www.lawfareblog.com/israeli-emergency-regulations-location-tracking-coronavirus-carriers
   INFO:root:rank=8 ranking=0.0000e+00 url=www.lawfareblog.com/why-congress-conducting-business-usual-face-coronavirus
   INFO:root:rank=9 ranking=0.0000e+00 url=www.lawfareblog.com/congressional-homeland-security-committees-seek-ways-support-state-federal-responses-coronavirus

   $ python3 pagerank.py --data=lawfareblog.csv.gz --search_query='trump'
   INFO:root:rank=0 ranking=1.4298e-08 url=www.lawfareblog.com/donald-trump-and-politically-weaponized-executive-branch
   INFO:root:rank=1 ranking=4.7393e-09 url=www.lawfareblog.com/did-donald-trump-jr-admit-violating-computer-fraud-and-abuse-act
   INFO:root:rank=2 ranking=2.6929e-09 url=www.lawfareblog.com/documents-saifullah-paracha-v-donald-j-trump
   INFO:root:rank=3 ranking=2.0187e-09 url=www.lawfareblog.com/cta9-decides-al-nashiri-v-macdonald
   INFO:root:rank=4 ranking=1.8208e-09 url=www.lawfareblog.com/donald-trump-danger-our-national-security
   INFO:root:rank=5 ranking=1.7227e-09 url=www.lawfareblog.com/burden-donald-trump
   INFO:root:rank=6 ranking=1.6886e-09 url=www.lawfareblog.com/does-trump-want-lose-eo-battle-court-or-donald-mcgahn-simply-ineffectual-or-worse
   INFO:root:rank=7 ranking=1.6787e-09 url=www.lawfareblog.com/nashiri-v-macdonald-dismissed
   INFO:root:rank=8 ranking=1.6725e-09 url=www.lawfareblog.com/more-donald-trump-and-justice-department
   INFO:root:rank=9 ranking=1.6718e-09 url=www.lawfareblog.com/donald-trump-paul-manafort-and-pesky-witness-tampering-statute

   $ python3 pagerank.py --data=lawfareblog.csv.gz --search_query='Iran'
   INFO:root:rank=0 ranking=2.8981e-07 url=www.lawfareblog.com/iranian-hostage-crisis-and-its-effect-american-politics
   INFO:root:rank=1 ranking=2.8366e-07 url=www.lawfareblog.com/and-then-there-was-one-tehran-still-has-one-iranian-american-behind-bars
   INFO:root:rank=2 ranking=2.6836e-07 url=www.lawfareblog.com/us-names-iranian-revolutionary-guard-terrorist-organization-and-sanctions-international-criminal
   INFO:root:rank=3 ranking=1.9256e-07 url=www.lawfareblog.com/trump-wants-bigger-better-deal-iran-what-does-tehran-want
   INFO:root:rank=4 ranking=1.9230e-07 url=www.lawfareblog.com/iranian-terrorism-victims-ask-court-block-release-iranian-assets-under-nuclear-deal
   INFO:root:rank=5 ranking=1.8720e-07 url=www.lawfareblog.com/afghanistan-another-victory-tehran
   INFO:root:rank=6 ranking=1.4129e-07 url=www.lawfareblog.com/iranian-protesters-strike-heart-regimes-revolutionary-legitimacy
   INFO:root:rank=7 ranking=1.0117e-07 url=www.lawfareblog.com/what-has-iran-done-now-primer-recent-iranian-missile-tests-and-sanctions
   INFO:root:rank=8 ranking=1.0044e-07 url=www.lawfareblog.com/two-further-notes-npt-and-iranian-legal-arguments
   INFO:root:rank=9 ranking=9.9820e-08 url=www.lawfareblog.com/iranian-missile-launch-and-gray-ladys-confusion
   ```

   Task 1, part 3:
   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz
   INFO:root:rank=0 ranking=2.8741e-01 url=www.lawfareblog.com/lawfare-job-board
   INFO:root:rank=1 ranking=2.8741e-01 url=www.lawfareblog.com/masthead
   INFO:root:rank=2 ranking=2.8741e-01 url=www.lawfareblog.com/litigation-documents-related-appointment-matthew-whitaker-acting-attorney-general
   INFO:root:rank=3 ranking=2.8741e-01 url=www.lawfareblog.com/documents-related-mueller-investigation
   INFO:root:rank=4 ranking=2.8741e-01 url=www.lawfareblog.com/topics
   INFO:root:rank=5 ranking=2.8741e-01 url=www.lawfareblog.com/about-lawfare-brief-history-term-and-site
   INFO:root:rank=6 ranking=2.8741e-01 url=www.lawfareblog.com/snowden-revelations
   INFO:root:rank=7 ranking=2.8741e-01 url=www.lawfareblog.com/support-lawfare
   INFO:root:rank=8 ranking=2.8741e-01 url=www.lawfareblog.com/upcoming-events
   INFO:root:rank=9 ranking=2.8741e-01 url=www.lawfareblog.com/our-comments-policy

   $ python3 pagerank.py --data=lawfareblog.csv.gz --filter_ratio=0.2
   INFO:root:rank=0 ranking=3.4696e-01 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
   INFO:root:rank=1 ranking=2.9521e-01 url=www.lawfareblog.com/livestream-nov-21-impeachment-hearings-0
   INFO:root:rank=2 ranking=2.9040e-01 url=www.lawfareblog.com/opening-statement-david-holmes
   INFO:root:rank=3 ranking=1.5179e-01 url=www.lawfareblog.com/lawfare-podcast-ben-nimmo-whack-mole-game-disinformation
   INFO:root:rank=4 ranking=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1963
   INFO:root:rank=5 ranking=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1964
   INFO:root:rank=6 ranking=1.5071e-01 url=www.lawfareblog.com/lawfare-podcast-week-was-impeachment
   INFO:root:rank=7 ranking=1.4957e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1962
   INFO:root:rank=8 ranking=1.4367e-01 url=www.lawfareblog.com/cyberlaw-podcast-mistrusting-google
   INFO:root:rank=9 ranking=1.4240e-01 url=www.lawfareblog.com/lawfare-podcast-bonus-edition-gordon-sondland-vs-committee-no-bull
   ```

   Task 1, part 4:

   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --verbose
   INFO:root:rank=0 ranking=2.8741e-01 url=www.lawfareblog.com/lawfare-job-board
   INFO:root:rank=1 ranking=2.8741e-01 url=www.lawfareblog.com/masthead
   INFO:root:rank=2 ranking=2.8741e-01 url=www.lawfareblog.com/litigation-documents-related-appointment-matthew-whitaker-acting-attorney-general
   INFO:root:rank=3 ranking=2.8741e-01 url=www.lawfareblog.com/documents-related-mueller-investigation
   INFO:root:rank=4 ranking=2.8741e-01 url=www.lawfareblog.com/topics
   INFO:root:rank=5 ranking=2.8741e-01 url=www.lawfareblog.com/about-lawfare-brief-history-term-and-site
   INFO:root:rank=6 ranking=2.8741e-01 url=www.lawfareblog.com/snowden-revelations
   INFO:root:rank=7 ranking=2.8741e-01 url=www.lawfareblog.com/support-lawfare
   INFO:root:rank=8 ranking=2.8741e-01 url=www.lawfareblog.com/upcoming-events
   INFO:root:rank=9 ranking=2.8741e-01 url=www.lawfareblog.com/our-comments-policy

   $ python3 pagerank.py --data=lawfareblog.csv.gz --verbose --alpha=0.99999
   INFO:root:rank=0 ranking=2.8859e-01 url=www.lawfareblog.com/lawfare-job-board
   INFO:root:rank=1 ranking=2.8859e-01 url=www.lawfareblog.com/masthead
   INFO:root:rank=2 ranking=2.8859e-01 url=www.lawfareblog.com/litigation-documents-related-appointment-matthew-whitaker-acting-attorney-general
   INFO:root:rank=3 ranking=2.8859e-01 url=www.lawfareblog.com/documents-related-mueller-investigation
   INFO:root:rank=4 ranking=2.8859e-01 url=www.lawfareblog.com/topics
   INFO:root:rank=5 ranking=2.8859e-01 url=www.lawfareblog.com/about-lawfare-brief-history-term-and-site
   INFO:root:rank=6 ranking=2.8859e-01 url=www.lawfareblog.com/snowden-revelations
   INFO:root:rank=7 ranking=2.8859e-01 url=www.lawfareblog.com/support-lawfare
   INFO:root:rank=8 ranking=2.8859e-01 url=www.lawfareblog.com/upcoming-events
   INFO:root:rank=9 ranking=2.8859e-01 url=www.lawfareblog.com/our-comments-policy

   $ python3 pagerank.py --data=lawfareblog.csv.gz --verbose --filter_ratio=0.2
   INFO:root:rank=0 ranking=3.4696e-01 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
   INFO:root:rank=1 ranking=2.9521e-01 url=www.lawfareblog.com/livestream-nov-21-impeachment-hearings-0
   INFO:root:rank=2 ranking=2.9040e-01 url=www.lawfareblog.com/opening-statement-david-holmes
   INFO:root:rank=3 ranking=1.5179e-01 url=www.lawfareblog.com/lawfare-podcast-ben-nimmo-whack-mole-game-disinformation
   INFO:root:rank=4 ranking=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1963
   INFO:root:rank=5 ranking=1.5099e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1964
   INFO:root:rank=6 ranking=1.5071e-01 url=www.lawfareblog.com/lawfare-podcast-week-was-impeachment
   INFO:root:rank=7 ranking=1.4957e-01 url=www.lawfareblog.com/todays-headlines-and-commentary-1962
   INFO:root:rank=8 ranking=1.4367e-01 url=www.lawfareblog.com/cyberlaw-podcast-mistrusting-google
   INFO:root:rank=9 ranking=1.4240e-01 url=www.lawfareblog.com/lawfare-podcast-bonus-edition-gordon-sondland-vs-committee-no-bull

   $ python3 pagerank.py --data=lawfareblog.csv.gz --verbose --filter_ratio=0.2 --alpha=0.99999
   INFO:root:rank=0 ranking=7.0149e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=1 ranking=7.0149e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=2 ranking=1.0552e-01 url=www.lawfareblog.com/cost-using-zero-days
   INFO:root:rank=3 ranking=3.1757e-02 url=www.lawfareblog.com/lawfare-podcast-former-congressman-brian-baird-and-daniel-schuman-how-congress-can-continue-function
   INFO:root:rank=4 ranking=2.2040e-02 url=www.lawfareblog.com/events
   INFO:root:rank=5 ranking=1.6027e-02 url=www.lawfareblog.com/water-wars-increased-us-focus-indo-pacific
   INFO:root:rank=6 ranking=1.6026e-02 url=www.lawfareblog.com/water-wars-drill-maybe-drill
   INFO:root:rank=7 ranking=1.6023e-02 url=www.lawfareblog.com/water-wars-disjointed-operations-south-china-sea
   INFO:root:rank=8 ranking=1.6020e-02 url=www.lawfareblog.com/water-wars-song-oil-and-fire
   INFO:root:rank=9 ranking=1.6020e-02 url=www.lawfareblog.com/water-wars-sinking-feeling-philippine-china-relations
   ```

   Task 2, part 1:

   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona'
   INFO:root:rank=0 ranking=6.3209e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=1 ranking=6.3206e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=2 ranking=1.5657e-01 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
   INFO:root:rank=3 ranking=1.2040e-01 url=www.lawfareblog.com/brexit-not-immune-coronavirus
   INFO:root:rank=4 ranking=1.2040e-01 url=www.lawfareblog.com/rational-security-my-corona-edition
   INFO:root:rank=5 ranking=9.1991e-02 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
   INFO:root:rank=6 ranking=8.9981e-02 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
   INFO:root:rank=7 ranking=8.9981e-02 url=www.lawfareblog.com/britains-coronavirus-response
   INFO:root:rank=8 ranking=7.6014e-02 url=www.lawfareblog.com/lawfare-podcast-united-nations-and-coronavirus-crisis
   INFO:root:rank=9 ranking=7.1742e-02 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
   ```

   Task 2, part 2:

   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona' --search_query='-corona'
   INFO:root:rank=0 ranking=0.0000e+00 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=1 ranking=0.0000e+00 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=2 ranking=0.0000e+00 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
   INFO:root:rank=3 ranking=0.0000e+00 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
   INFO:root:rank=4 ranking=0.0000e+00 url=www.lawfareblog.com/lawfare-podcast-mom-and-dad-talk-clinical-trials-pandemic
   INFO:root:rank=5 ranking=0.0000e+00 url=www.lawfareblog.com/fault-lines-foreign-policy-quarantined
   INFO:root:rank=6 ranking=0.0000e+00 url=www.lawfareblog.com/limits-world-health-organization
   INFO:root:rank=7 ranking=0.0000e+00 url=www.lawfareblog.com/chinatalk-dispatches-shanghai-beijing-and-hong-kong
   INFO:root:rank=8 ranking=0.0000e+00 url=www.lawfareblog.com/us-moves-dismiss-case-against-company-linked-ira-troll-farm
   INFO:root:rank=9 ranking=0.0000e+00 url=www.lawfareblog.com/livestream-house-armed-services-holds-hearing-national-security-challenges-north-and-south-america
   ```
