
## Install Pods

 1️⃣ Go to the iOS build folder

`cd /Users/administrator/Documents/ProGolf/ProGolfiOS/Builds/iOSBuild`

---

 2️⃣ Completely remove old Pods & caches

`rm -rf Pods` 
`rm -rf Podfile.lock`
`rm -rf *.xcworkspace`

(Optional but recommended)

`rm -rf ~/Library/Developer/Xcode/DerivedData`

---

3️⃣ Deintegrate CocoaPods (safe even if Pods folder is gone)

`pod deintegrate`

---

4️⃣ Update CocoaPods repo (important for new SDKs)

`pod repo update`

---

 5️⃣ Install Pods (fresh)

`pod install`