---
title: Style_Guides
permalink: Develop/L10n/Style_Guides/

---

Having a style guide massively improves translations for a given
language, consistency, mood, voice, you name it. We strongly encourage
all Sailfish OS languages to have one.

Existing style guides are [listed
here](/Develop/L10n). Guides of existing community
languages progress is in this [TJC
post](https://together.jolla.com/question/145988/official-announcement-contribute-language-style-guides-not-a-question/).

To create a guide for a new language, please take e.g. [English (United
Kingdom)](/Develop/L10n/Style_Guides/English_(United_Kingdom)) as
reference, view [its
source](https://sailfishos.org/wiki/index.php?title=Language_Style_-_English_\(United_Kingdom\)&action=edit),
and copy to your text editor. You'll need to work "offline" for the time
being, apologies; contributions to the wiki will become more
straightforward in the future.

Then start shaping its contents to match your language grammar and
culture.

You'll see existing style guides peppered with templates for maximum
re-use, e.g.

    {{Style_grammar_voice}}
    For example:
    * Correct: '''Create Account Settings in...'''
    * Incorrect: '''Account Settings are created in...'''

You can view the contents of this template like so:
[Template:Style\_grammar\_voice](/Template:Style_grammar_voice)

If your language has a different rule than the template says (e.g.
passive voice preferred over active), simply replace with [template's
source](https://sailfishos.org/wiki/index.php?title=Template:Style_grammar_voice&action=edit):

    == Voice ==
    Whenever possible, use the passive voice. Keep the message clear and the sentences short
    
    For example:
    * Correct: '''<an example of passive voice in your language>'''
    * Incorrect: '''<an example of active voice in your language>'''

Then carry on through all other sections in the same fashion, if you
have doubts, open tickets in TJC to consult the fellow speakers (tag
with `translate` and your language name e.g. `dutch`. If you feel like
some sections are not relevant or lack information, it's ok to skip
them, someone else will complement them in the future.

Currently contributions to Sailfish OS wiki are going through a
reviewing person. You'll need to [email
me](http://simonas_dot_leleiva_at_jolla_dot_com) the style guide and
I'll place it next to others crediting your contribution.

Unfortunately because the wiki user registration is also disabled, you
cannot preview your created articles :( I'll make sure to polish any
visual imperfections after receiving your source. You can send me any
corrections thereafter as well.
