# README
[Words Please](https://wordsplease.github.io/words-please-tutorial/)

Words Please is a sentence forming app that children with speech difficulties whose age ranges from 3 to 6 will be able to use on their iOS device in conjunction with their speech therapist or AIDE. Each phrase comes with text-to-audio to reinforce speech.

## Key Features

+ Forming sentences
  + Sentences are divided into segments or phrases. When given a sentence starter, the appropriate text or phrase will be used to follow up, which the student can select and eventually form a completed sentence.
![boardgif](https://res.cloudinary.com/dqj3kgpoj/image/upload/v1541535528/wordsplease.gif)

+ Settings
  + The child is able to use this app throughout their entire school period as there are two settings: classroom and playground. Each setting has a particular set of words attached to it; `on the swings` would be a word that a child would associate with during recess, so it's unavailable to be asked during the classroom setting. This is done by creating a joins table of the last card (titled finishers) and the setting.
   ```js
   class SettingMembership < ApplicationRecord

     validates :setting_id, :finisher_id, presence: true

     belongs_to :setting,
     foreign_key: :setting_id,
     class_name: :Setting

     belongs_to :finisher,
     foreign_key: :finisher_id,
     class_name: :Finisher
   end
   ```

  + Audio
    + After forming a sentence, the child will be coached by their therapist or aide to finish the sentence. After tapping the sentence, an audio voice will voice the sentence for the student to repeat after. This is to reinforce speech.

  ```js
  <TouchableOpacity
    onPress={()=> {
      Tts.speak(activeSet[0], { iosVoiceId: 'com.apple.ttsbundle.Samantha-compact' })
    }}>
    <Text>
      {activeSet[0]}
    </Text>
  </TouchableOpacity>
  <View style={{flex: 3, flexDirection: 'row', backgroundColor: '#3498DB'}}>

    {activeSet[1]}
  </View>
  ```

### Challenges
One of the challenges was working together for the first time as this was the first time we all worked together in a group. We divided the project into several steps and components and made each person responsible for a specific portion. However, when there were disagreements, it would be difficult to communicate as an issue for one would cause an issue for another. We often came together to work out problems when an issue rose.

## Future Direction/Features
Future updates will include:
+ CSS fixes
+ Create feature so users can add their own card
+ Scroll function
+ More settings
