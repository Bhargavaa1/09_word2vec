# Word2Vec Project

In this project, you will create a simple search engine for the website <https://www.lawfareblog.com>.
This website provides legal analysis on US national security issues.

**Due date:** Sunday, 11 December at midnight

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
   INFO:root:rank=0 pagerank=4.6096e+00 url=www.lawfareblog.com/trump-asks-supreme-court-stay-congressional-subpeona-tax-returns
   INFO:root:rank=1 pagerank=2.9870e+00 url=www.lawfareblog.com/livestream-nov-21-impeachment-hearings-0
   INFO:root:rank=2 pagerank=2.9672e+00 url=www.lawfareblog.com/opening-statement-david-holmes
   INFO:root:rank=3 pagerank=2.0175e+00 url=www.lawfareblog.com/senate-examines-threats-homeland
   INFO:root:rank=4 pagerank=1.8771e+00 url=www.lawfareblog.com/what-make-first-day-impeachment-hearings
   INFO:root:rank=5 pagerank=1.8764e+00 url=www.lawfareblog.com/livestream-house-armed-services-committee-hearing-f-35-program
   INFO:root:rank=6 pagerank=1.8695e+00 url=www.lawfareblog.com/whats-house-resolution-impeachment
   INFO:root:rank=7 pagerank=1.7657e+00 url=www.lawfareblog.com/congress-us-policy-toward-syria-and-turkey-overview-recent-hearings
   INFO:root:rank=8 pagerank=1.6809e+00 url=www.lawfareblog.com/summary-david-holmess-deposition-testimony
   INFO:root:rank=9 pagerank=9.8355e-01 url=www.lawfareblog.com/events

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
   INFO:root:rank=0 pagerank=5.2386e+01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=1 pagerank=5.2386e+01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=2 pagerank=7.9439e+00 url=www.lawfareblog.com/cost-using-zero-days
   INFO:root:rank=3 pagerank=2.3700e+00 url=www.lawfareblog.com/lawfare-podcast-former-congressman-brian-baird-and-daniel-schuman-how-congress-can-continue-function
   INFO:root:rank=4 pagerank=1.5530e+00 url=www.lawfareblog.com/events
   INFO:root:rank=5 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-increased-us-focus-indo-pacific
   INFO:root:rank=6 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-drill-maybe-drill
   INFO:root:rank=7 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-disjointed-operations-south-china-sea
   INFO:root:rank=8 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-us-china-divide-shangri-la
   INFO:root:rank=9 pagerank=1.1867e+00 url=www.lawfareblog.com/water-wars-sinking-feeling-philippine-china-relations
   ```

   Task 2, part 1:

   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona'
   INFO:root:rank=0 pagerank=8.8870e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=1 pagerank=8.8867e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=2 pagerank=1.8256e-01 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
   INFO:root:rank=3 pagerank=1.4907e-01 url=www.lawfareblog.com/brexit-not-immune-coronavirus
   INFO:root:rank=4 pagerank=1.4907e-01 url=www.lawfareblog.com/rational-security-my-corona-edition
   INFO:root:rank=5 pagerank=1.0729e-01 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
   INFO:root:rank=6 pagerank=1.0199e-01 url=www.lawfareblog.com/britains-coronavirus-response
   INFO:root:rank=7 pagerank=1.0199e-01 url=www.lawfareblog.com/prosecuting-purposeful-coronavirus-exposure-terrorism
   INFO:root:rank=8 pagerank=9.4298e-02 url=www.lawfareblog.com/lawfare-podcast-mom-and-dad-talk-clinical-trials-pandemic
   INFO:root:rank=9 pagerank=8.7207e-02 url=www.lawfareblog.com/house-oversight-committee-holds-day-two-hearing-government-coronavirus-response
   ```

   Task 2, part 2:

   ```
   $ python3 pagerank.py --data=lawfareblog.csv.gz --filter_ratio=0.2 --personalization_vector_query='corona' --search_query='-corona'
   INFO:root:rank=0 pagerank=8.8870e-01 url=www.lawfareblog.com/covid-19-speech-and-surveillance-response
   INFO:root:rank=1 pagerank=8.8867e-01 url=www.lawfareblog.com/lawfare-live-covid-19-speech-and-surveillance
   INFO:root:rank=2 pagerank=1.8256e-01 url=www.lawfareblog.com/chinatalk-how-party-takes-its-propaganda-global
   INFO:root:rank=3 pagerank=1.0729e-01 url=www.lawfareblog.com/trump-cant-reopen-country-over-state-objections
   INFO:root:rank=4 pagerank=9.4298e-02 url=www.lawfareblog.com/lawfare-podcast-mom-and-dad-talk-clinical-trials-pandemic
   INFO:root:rank=5 pagerank=7.9633e-02 url=www.lawfareblog.com/fault-lines-foreign-policy-quarantined
   INFO:root:rank=6 pagerank=7.5307e-02 url=www.lawfareblog.com/limits-world-health-organization
   INFO:root:rank=7 pagerank=6.8115e-02 url=www.lawfareblog.com/chinatalk-dispatches-shanghai-beijing-and-hong-kong
   INFO:root:rank=8 pagerank=6.4847e-02 url=www.lawfareblog.com/us-moves-dismiss-case-against-company-linked-ira-troll-farm
   INFO:root:rank=9 pagerank=6.4847e-02 url=www.lawfareblog.com/livestream-house-foreign-affairs-committee-holds-hearing-crisis-idlib
   ```
