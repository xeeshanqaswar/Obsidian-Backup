

- so problem currently is in case of fail attempt the sequence and execution remains the as it was remains before introducing enableEndScreen boolean, I specifically told you comming back tee was only for success case. I believe I also made mistake by instructing you initially that only show endcard if enableEndScreen is set true eventhrough right know we are utilizing it. so I thinl we should remove the enableEndScreen variable and instead instroduce an option called "noEndScreen" in endScreenPrefab dropdown along side standard, iphone and Characters 

- Currently when you successfuly complete the hole there are two different camera movements happening First during celebration and than it translates to tee, instead of that it should be one smooth camera transition from hole to tee