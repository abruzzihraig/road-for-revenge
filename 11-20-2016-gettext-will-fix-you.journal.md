### Gettext Will Fix You
My friend Dolphin analyzed my journals and found the keyword 'game' comes more than 50 times(But actually it just exists in 30 articles). No matter what it makes me awkward. Then I did the same thing and found more than 20 articles related to Dark Souls. Known that made me feel innocent, because the DarkSouls series(includes Bloodborne) are entirely arts, and Hidetaka Miyazaki is the best genius in video game creating. I don't mind if I will pay more than three hundred hours on each game from him.

Meanwhile, I really want to do some significant stuff for myself. Because I don't want someday when I become old will be test human nature from family or society then, I don't want to see the scenario just due to lack of money. Hope everyone I met will keep kindness forever. Hope each friend I met will not become a man/woman like a scheming questioner in Zhihu. I've already seen much sorrow in the first half of my life.

Nearly night, a friend asked me why I choose GNU Gettext to handle internationalization on the web rather than a typical dictionary solution. I thought a little and answered to him that GNU Gettext has three advantages than a dictionary. They are context, plural, and interpolation. I thought my reply is the key point to explain another similar question why we will choose GNU Gettext.

I know you can make a dictionary better and add some useful features to your personal solution, and it even might be better than GNU Gettext. But the GNU Gettext is just a standard. It thinks more than a regular developer. The difference is just like why we choose to use OAuth.

The GNU Gettext supports context, which means you can control every word you want to translate in an accurate context. For example, the same word in English could have a different meaning in other languages, so that the same English word displayed on different pages may need to translate to a different word in other languages.

The 'plural' question has a little bit of like the context above. Some languages are sensitive with singular and plural. For example, in English, we use the form 'one day' but 'two days.' However, in Chinese, they are same with 'N 天'.

As for the interpolation, you might have already guessed what does the Gettext do. Different languages may have different grammar, and the various grammar form could have different structure and order in one sentence. So in GNU Gettext you could use a sentence with interpolation as a key of the original dictionary, it usually is English dictionary. Especially when you write something like 'Hello {{name}}' in English, but you want to change the structure in Chinese like '{{name}}, 你好.'

Another benefit from GNU Gettext is there are lots of PO editors you could use for editing different language dictionaries.

That's why I recommend developers to use the standard GNU Gettext to handle internationalization rather than recreate another solution by themselves with some traps.

Time to sleep, Good night!
