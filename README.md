# FilCo

<p align="left">
  <a href="http://creativecommons.org/licenses/by-sa/4.0/"><img src="https://img.shields.io/badge/License-CC%20BY--SA%204.0-green.svg"></a>
  <a href="https://arxiv.org/abs/2311.08377"><img src="https://img.shields.io/badge/arXiv-2311.08377-b31b1b.svg"></a>
</p>

This repository contains the code and data about the project:
[Learning to Filter Context for Retrieval-Augmented Generation](https://arxiv.org/pdf/2311.08377.pdf)

# 多条回答

在NLP中的问答任务中，**多条回答**（multiple answers）指的是系统为一个问题生成或提供多种不同的有效答案。这种情况常见于开放域问答任务中，尤其是以下几种场景：

### 1. **同一问题有多种解释**

- 有时，一个问题可能会有多个合理的答案。尤其在复杂的、没有明确单一正确答案的问题中，系统可能会提供多个有效的解释。
- **例子**:
  - **问题**: "What causes climate change?"
  - **回答 1**: "Increased greenhouse gas emissions."
  - **回答 2**: "Deforestation and industrial activities."

### 2. **答案形式的不同**

- 即使答案内容相同，系统可能以不同的语言或结构表述。例如，有些模型会生成详细的回答，而有些则会生成简短的答案。
- **例子**:
  - **问题**: "What is photosynthesis?"
  - **回答 1**: "Photosynthesis is the process by which plants use sunlight to convert carbon dioxide and water into glucose and oxygen."
  - **回答 2**: "It's the process where plants make food using sunlight."

### 3. **检索系统的多条证据**

- 对于一些需要引用证据的问答任务，模型可能会提供多个证据来源或多个回答，每个回答基于不同的文档或背景知识。
- **例子**:
  - **问题**: "Who invented the telephone?"
  - **回答 1**: "Alexander Graham Bell is widely credited with inventing the telephone."
  - **回答 2**: "Some argue that Antonio Meucci was the first to develop a device resembling a telephone."

### 4. **不确定性和多样性**

- 在某些情况下，问题的答案可能本身带有不确定性（如预测类问题），或者问题本身具有开放性。为此，模型可能会提供多种可能的答案，帮助用户理解不同的答案选项。
- **例子**:
  - **问题**: "What will be the global population in 2050?"
  - **回答 1**: "The global population is projected to be around 9.7 billion."
  - **回答 2**: "Estimates range from 9 to 10 billion depending on fertility rates."

### 5. **生成式模型中的多样性答案**

- 在生成式任务中，模型可能通过不同的生成策略（如改变温度参数）生成多个不同的答案，增加回答的多样性和丰富性。
- **例子**:
  - **问题**: "How do you bake a cake?"
  - **回答 1**: "Mix flour, sugar, eggs, and butter, then bake at 350°F for 30 minutes."
  - **回答 2**: "Combine ingredients like flour, sugar, eggs, and butter, bake at 180°C for 40 minutes."

### 6. **问答数据集的多条标注**

- 在某些问答数据集中（如 SQuAD），一个问题可能有多个由人工标注的参考答案，以捕捉不同的可能性。这帮助模型学习不同的表述方式。
- **例子**:
  - **问题**: "When was the Declaration of Independence signed?"
  - **回答 1**: "It was signed on July 4, 1776."
  - **回答 2**: "The signing took place on July 4th, 1776."

### **总结**

多条回答能让系统更灵活地应对复杂问题，提升模型在实际场景中的实用性。RAG 模型通过检索和生成的结合，能够为用户提供多种可能的回答，增强信息的全面性和准确性。

# 数据集

这些数据集广泛用于自然语言处理（NLP）和检索增强生成（RAG）模型的训练与评估。以下是每个数据集的简要说明：

### 1. **ELI5 (Explain Like I’m 5)**

- **类型**: Long-Form 问答数据集，generative question
- **实验设置：** generate short
- **测试指标：** uni-gram F1
- **描述**: ELI5 数据集来自 Reddit 的 "Explain Like I'm 5" 子版块，问题通常是用户提出的开放性问题，回答者尝试以简单、易懂的方式来解释复杂问题。这个数据集的重点是生成长篇的答案，适合生成式任务和信息检索任务。
- **应用场景**: 用于开放域问答，尤其是在需要生成解释性答案的场景下。

  ```json
   {
          "question": "In Trading Places (1983, Akroyd/Murphy) how does the scheme at the end of the movie work? Why would buying a lot of OJ at a high price ruin the Duke Brothers?",
          "answers": [
              "The final scene involves future contracts. This simply means entering into a contract to buy something (oil, wheat, even frozen concentrated orange juice(FCOJ)) at a specified time for the current price. The person selling the future does not have to own the FCOJ at the time of sale he simply has to provide them at the agreed upon date. Futures help companies mitigate risk against the unpredictable price of FCOJ. If the price of FCOJ goes up the buyer wins the seller loses and visa versa. This price is often affected by fresh oranges. If there is a good harvest FCOJ price goes down and so on. The Dukes believed there was going to be a bad harvest. Their plan was to buy as much FCOJ as they could and basically corner the market then sell it at a much higher price due to a lack of oranges. So here is what happened. At first Winthrop and Valentine begin selling futures contracts at inflated prices caused by the Dukes (on the info from the fake report of a bad orange harvest) at approximately $1.45 per unit. When the report comes out that the orange harvest is expected to be good caused a massive selloff and the futures price plummeted to about $.22 cents. This is when Winthrop and Valentine begin buying futures instead of selling. So now they can fill the futures orders of $1.45 with oranges costing $.22 earning something like a 545% profit.",
              "They had an episode of Marketplace that addressed this a few weeks ago:  URL_0 ",
              "NPR actually did a interview explaining everything pretty well.  URL_0 ",
              "If I remember correctly, they knew that the price of orange juice was going to fall. Normally this wouldn't matter, because you are supposed to buy and hold stocks, but they were buying what's called 'futures'. In a nutshell, they were buying contracts that afford them the legal right to purchase units of OJ at a specific price. Since they knew the price of OJ would fall (remember the dude with the locked briefcase?) they were buying option contracts to purchase OJ at a higher price. Anyone with half a brain would sell them these and of course that's what happened. For in depth knowledge, look up \"how futures trading works.\"",
              "The unrealistic part of that flick is not the trading but Winthorp and Valentine being able just to waltz in to that pit and stand wherever they want. Spots in a commodity pit are protected like gang turf. They just go in and stand in the middle. Also if they deposit the cash from everyone's savings lets say 100k and the margin per contract is 5k per contract they can only buy or sell 20 contracts. I don't know what the FCOJ margins are, but if they trade more than 20 the profit goes to the exchange. At least that's how the CME rolls.",
              "Fun fact: In \"Coming to America\", when Akeem's character gave the money to the 2 homeless guys, it was the Duke brothers. :)  URL_0 ",
              "odd things I noted - 1. They didn't go in with that much cash. I understand they first sold high and then bought low. So how did they sell so much with just a small sum? They should've bought very little contracts of fcoj which would sell out in 1min with that frenzy and then the buyers would go somewhere else and price would rise even beyond $1.42 2. They all look at the clock and then 9am (I think) strikes and crop report is read. Then they all panic because they need to unload whatever they bought and finding the 2 buying they sell ASAP. Again how can these 2 buy everything with so little money? 3. Finally the closing bell strikes and trading stops. How did all this scheme happen so fast ? Doesnt trading happen 9:30am to 4pm at NYSE (why wtc was shown?) for such commodities. Did they spend that many hours there? It just seemed sudden and abrupt the time flow.",
              "it was the margin call for the duke brothers. as i'm sure others explained, the dukes shorted the market based on info from the phony crop report. so when the price shot up, a margin call was due, even after the price settled a bit after billy and louie sold their holdings for huge gains. when the market closed with the price still up, the movie shows the guy affiliated with the exchange saying \"Margin call.\". In reality I think it would've been the firm that they trade through and that provided them the loan in the first place. (margin call means pay back the loaned amount) edit: maybe I had it backwards and the dukes were going to go long on OJ futures, but it's the same principle. margin call did them in after the market worked against them based on their false knowledge.",
              "I feel so old. People have been askinbg what happened at the end of this movie for what must be the last 15 years of my life. It never stops. Every year/month/fortnight, I see someone asking what happened, and someone explaining. Andf it will keep on happening, until I am 90yrs old, in a home, with nothing but the Internet and my bladder to keep me going. And there it will be: \"what happens at the end of Trading Places?\""
          ],
          "ctxs": [
              {
                  "id": "wiki:7780062",
                  "title": "No Deposit, No Return",
                  "text": "she left, she made plans that the two children spend the vacation with their grandfather, Los Angeles billionaire J.W Osborne. Neither the children nor Osborne are enthused. Osborne, who has bad experiences with the children, takes steps to ensure the same level of chaos is not repeated. During the plane trip, Jay realizes he has mislaid his pet skunk, Duster. In the horror and panic ensuing from the loss, Osborne's loyal butler, Mr. Jamieson, fails to meet them at the airport, and the children make their escape in a taxi. Meanwhile, at the same airport, safe-crackers and robbers Duke and",
                  "score": "74.549515"
              },
              {
                  "id": "wiki:2792381",
                  "title": "Trading Places",
                  "text": "position by buying futures at the lower price from everyone but the Dukes, turning a large profit. The Dukes fail to meet a margin call, and are left owing $394 million. Valentine and Winthorpe explain to the Dukes that they had made a wager on whether they could simultaneously get rich while making the Dukes poor. Valentine collects $1 from Winthorpe while Randolph collapses holding his chest and Mortimer shouts angrily at his brother about their failed plan. Later, the now wealthy Valentine, Winthorpe, Ophelia, and Coleman vacation on a tropical beach, while Beeks and the gorilla are loaded onto",
                  "score": "73.88309"
              },
              {
                  "id": "wiki:17219793",
                  "title": "Papadopoulos & Sons",
                  "text": "empire in the food industry. But when the banking crisis hits, Harry and his family - shy horticulturist James, snobby fashion victim Katie, and precocious child prodigy Theo - lose everything. Everything, except the dormant and forgotten Three Brothers Fish & Chip Shop half-owned by Harry´s larger-than-life brother Spiros who's been estranged from the family for years. With no alternative, Harry and his family are forced to pack their bags and reluctantly join `Uncle Spiros´ to live above the neglected Three Brothers chippie. Together they set about bringing the chip shop back to life under the suspicious gaze of their",
                  "score": "73.182526"
              },
              {
                  "id": "wiki:2792378",
                  "title": "Trading Places",
                  "text": "the business using his street smarts to achieve success, and begins to act well-mannered. During the firm's Christmas party, Winthorpe is caught planting drugs in Valentine's desk in an attempt to frame him, and he brandishes a gun to escape. Later, the Dukes discuss their experiment and settle their wager for one dollar, before plotting to return Valentine to the streets. Valentine overhears the conversation, and seeks out Winthorpe, who attempts suicide by overdosing on pills. Valentine, Ophelia and Winthorpe's butler Coleman nurse him back to health and inform him of the Dukes' experiment. On television, they learn that Clarence",
                  "score": "73.15421"
              },
              {
                  "id": "wiki:14357207",
                  "title": "Of Love & Betrayal",
                  "text": "his attentions to Portia. When Sandy and Portia realize that Jack has seduced each of them in turn and convinced each to reveal to him the name of the island on her coin, they turn on him. Feeling betrayed and realizing that they no longer need Jack in order to sail the boat or find the gold, they maroon him on a small island and go after the sunken treasure themselves. Jack is rescued by a local fisherman whose radio alerts him of Hurricane Andrew. The building gale is expected to be an infamous once-in-a-hundred-years storm. And it is headed",
                  "score": "72.87062"
              }
          ]
      },
  ```

### 2. **FEVER (Fact Extraction and VERification)**

- **类型**: 事实验证数据集
- **测试指标：** accurate
- **描述**: FEVER 数据集用于事实验证任务，包含人类编写的句子和相应的维基百科证据，任务是判断陈述是否为真、假或无证据支持。这是构建文本推理和事实验证模型的重要资源。
- **应用场景**: 事实验证、信息检索和文档级别的证据发现。

  ```json
  {
          "question": "Hot Right Now is from the album Escape from Planet Monday.",
          "answers": [
              "REFUTES"
          ],
          "ctxs": [
              {
                  "id": "wiki:4653365",
                  "title": "Manic Monday",
                  "text": "Manic Monday \"Manic Monday\" is a song by the American pop rock band The Bangles, and the first single released from their second studio album, \"Different Light\" (1986). It was written by American musician Prince, using the pseudonym \"Christopher\". Originally intended for the group Apollonia 6 in 1984, he offered the song to The Bangles two years later. Lyrically, it describes a woman who is waking up to go to work on Monday, wishing it were still Sunday so she could instead relax. The song, which was released on Monday January 27, 1986 by Columbia Records, received generally positive reviews",
                  "score": "77.31693"
              },
              {
                  "id": "wiki:9979164",
                  "title": "Planet Rock (song)",
                  "text": "Planet Rock (song) \"Planet Rock\" (also known as \"Don't Stop... Planet Rock\") is a 1982 song by Afrika Bambaataa & the Soulsonic Force. The song featured Marvella Murray, Yvette Murray, Melissa Johnson and Sandra Wheeler on additional background vocals. Although it was primarily an underground hit in the United States, Canada, and UK, it helped change the foundations of hip-hop and dance music and became one of the most influential pieces and a milestone and eventually an icon of the hip-hop, breakdance and electronic music cultures. It is credited with pioneering the genre and developing the electro style, building on",
                  "score": "75.79452"
              },
              {
                  "id": "wiki:4450318",
                  "title": "Emergency on Planet Earth",
                  "text": "from album liner notes. !scope=\"row\"|Worldwide (IFPI) Emergency on Planet Earth Emergency on Planet Earth is the debut studio album released by British funk/acid jazz band Jamiroquai, released on 14 June 1993 in both Japan and the United Kingdom and 10 August 1993 in the United States. The recurring theme on the album deals with lyrics about world issues and self-consciousness, along with several jazz instrumentals that made the album a success in the band's native country. The album produced singles, including \"Too Young To Die\" and \"Blow Your Mind\". The album was listed in the \"1001 Albums You Must Hear",
                  "score": "75.35513"
              },
              {
                  "id": "wiki:18391318",
                  "title": "Uptown Funk",
                  "text": "Uptown Funk \"Uptown Funk\" (stylised as \"UpTown Funk!\") is a song recorded by British record producer Mark Ronson featuring American singer and songwriter Bruno Mars, for Ronson's fourth studio album, \"Uptown Special\" (2015). RCA Records released the song as the album's lead single on 10 November 2014. Jeff Bhasker assisted the artists in co-writing and co-producing the track, with additional writing from Philip Lawrence. The song became a worldwide phenomenon with its major impact on pop culture. The song went through many different incarnations, and was worked on for months. Ronson and Mars recorded it at multiple different locations worldwide,",
                  "score": "75.29644"
              },
              {
                  "id": "wiki:4450316",
                  "title": "Emergency on Planet Earth",
                  "text": "Emergency on Planet Earth Emergency on Planet Earth is the debut studio album released by British funk/acid jazz band Jamiroquai, released on 14 June 1993 in both Japan and the United Kingdom and 10 August 1993 in the United States. The recurring theme on the album deals with lyrics about world issues and self-consciousness, along with several jazz instrumentals that made the album a success in the band's native country. The album produced singles, including \"Too Young To Die\" and \"Blow Your Mind\". The album was listed in the \"1001 Albums You Must Hear Before You Die\" list. \"Entertainment Weekly",
                  "score": "75.27236"
              }
          ]
      }
  ```

### 3. **HotpotQA**

- **类型**: 多跳问答数据集（短答案），abstractive generation(answers o do not always appear in the ground-truth supporting documents P)
- **测试指标：** uni-gram F1
- **描述**: HotpotQA 是一个多跳问答数据集，要求系统从多个文档中提取相关信息来回答问题。与其他问答数据集不同，HotpotQA 特别关注问题需要跨越多个文档或段落才能得出答案。
- **应用场景**: 用于训练和评估需要多跳推理的问答模型。

  ```json

  [
      {
          "question": "What year did Guns N Roses perform a promo for a movie starring Arnold Schwarzenegger as a former New York Police detective?",
          "answers": [
              "1999"
          ],
          "ctxs": [
              {
                  "id": "wiki:6106601",
                  "title": "Guns N' Roses",
                  "text": "a full-time member. Reed was previously bandmates with Sorum in Johnny Crash. Guns N' Roses band fired its manager, Alan Niven, replacing him with Doug Goldstein in May 1991. According to a 1991 cover story by \"Rolling Stone\", Rose forced the dismissal of Niven against the wishes of some of his bandmates by refusing to complete the albums until he was replaced. The band released the recordings as two albums, \"Use Your Illusion I\" and \"Use Your Illusion II,\" on September 17, 1991. The tactic paid off when the albums debuted at No. 2 and No. 1 respectively in the",
                  "score": "72.99817"
              },
              {
                  "id": "wiki:2161565",
                  "title": "Rosanna Arquette",
                  "text": "the Rosanna in the song \"Rosanna\"?'\" Following the commercial and critical success of Lawrence Kasdan's \"Silverado\" in 1985, and the failure of both \"After Hours\" and \"8 Million Ways to Die\", she quit Hollywood to work in Europe, acting in Luc Besson's \"The Big Blue\" (1988). In 1989, director Martin Scorsese offered her a part in \"New York Stories\". Other movies of note are \"Pulp Fiction\" and the David Cronenberg film \"Crash\" and the Australian film \"Wendy Cracked a Walnut\" (1990) (also known as \"…Almost\"). In 1990, Arquette appeared on the cover and in a nude pictorial in \"Playboy\"'s September",
                  "score": "72.55498"
              },
              {
                  "id": "wiki:5535319",
                  "title": "Love Gun",
                  "text": "cardboard \"Love Gun\" (assembly required) was included inside the album, along with a Kiss merchandise order form. Before \"Love Gun\" was completed, a Gallup poll indicated that Kiss was the most popular band in the United States, beating Aerosmith, Led Zeppelin and the Eagles. On August 26, 27, and 28 1977, Kiss recorded three shows at the LA Forum for their next release, the live album \"Alive II\". The album cover was painted by fantasy artist Ken Kelly, who previously contributed the cover for 1976's \"Destroyer\". Written by Paul Stanley, \"I Stole Your Love\" is in the same vein as",
                  "score": "72.18176"
              },
              {
                  "id": "wiki:1323285",
                  "title": "Axl Rose",
                  "text": "court against Steven Adler, who had filed a lawsuit contending that he had been illegitimately fired. When the judge ruled against Rose, he agreed to an out-of-court settlement of $2,500,000 and 15% of the royalties for everything Adler recorded prior to his departure. In November of that year, Guns N' Roses released \"\"The Spaghetti Incident?\"\" a cover album of mostly punk songs, which proved less successful than its predecessors. Rose had included the hidden track \"Look at Your Game, Girl\", a song written by convicted murderer Charles Manson, which he intended as a personal message to his ex-girlfriend Stephanie Seymour.",
                  "score": "72.15253"
              },
              {
                  "id": "wiki:2484651",
                  "title": "Steven Tyler",
                  "text": "from producer Bruce Fairbairn. Aerosmith released \"Permanent Vacation\" in 1987, which became a huge multiplatinum success and launched three top-20 hits (\"Dude (Looks Like a Lady)\", \"Angel\", and \"Rag Doll\"). The band launched a tour with the emerging Guns N' Roses, opening many shows. \"Permanent Vacation\" was followed by 1989's \"Pump\", which was even more successful, selling 7 million copies and producing three top-10 hits (\"Love in an Elevator\", \"Janie's Got a Gun\", and \"What it Takes\") and one top-40 hit (\"The Other Side\"). \"Pump\" in particular had Tyler expand his musical horizons, co-writing the innovative hit \"Janie's Got a",
                  "score": "72.12266"
              }
          ]
      },
      {
          "question": "Are Random House Tower and 888 7th Avenue both used for real estate?",
          "answers": [
              "no"
          ],
          "ctxs": [
              {
                  "id": "wiki:11756872",
                  "title": "Random House Tower",
                  "text": "Random House Tower The Random House Tower, also known as the Park Imperial Apartments, is a 52-story mixed-use tower in New York City, United States, that is used as the American headquarters of book publisher Penguin Random House and a luxury apartment complex. The PRH entrance is on Broadway and goes up to 27 floors, while the apartment complex entrance is on West 56th Street. Separate architects designed each of the sections. Skidmore, Owings & Merrill designed the office portion, which has a steel frame. Ismael Leyva Architects and Adam D. Tihany designed the residential portion, which has a concrete",
                  "score": "78.48885"
              },
              {
                  "id": "wiki:12004918",
                  "title": "888 7th Avenue",
                  "text": "888 7th Avenue 888 7th Avenue is a 628 ft (191m) tall modern-style office skyscraper in Midtown Manhattan which was completed in 1969 and has 46 floors. Emery Roth & Sons designed the building, which is tied with Central Park Place for the 65th tallest building in New York City. It currently carries the Vornado Realty Trust corporate headquarters. Previously known as the Arlen Building, its namesake being the company responsible for its construction, Arlen Realty & Development Corporation. The Red Eye Grill is located in the building at street level. Moed de Armas renovated the Lobby, Elevators & Plaza",
                  "score": "77.99477"
              },
              {
                  "id": "wiki:11756875",
                  "title": "Random House Tower",
                  "text": "housing 130 apartments, as well as of retail space. In looking to expand its headquarters, Random House had originally planned to build a tower at 45th and Broadway across from its parent company Bertelsmann's headquarters at 1540 Broadway with a neon-lighted skyway across 45th Street connecting them. Random House Tower The Random House Tower, also known as the Park Imperial Apartments, is a 52-story mixed-use tower in New York City, United States, that is used as the American headquarters of book publisher Penguin Random House and a luxury apartment complex. The PRH entrance is on Broadway and goes up to",
                  "score": "76.78614"
              },
              {
                  "id": "wiki:12022594",
                  "title": "750 7th Avenue",
                  "text": "for the 74th tallest building in New York City. It is also LEED certified. In April 2011, Fosterlane Management from Kuwait announced they would be purchasing the building from Hines for $485 million. 750 7th Avenue 750 Seventh Avenue is a 615 ft (187m) tall Class-A office skyscraper in New York City. It was completed in 1989 in the postmodern style and has 36 floors. Kevin Roche John Dinkeloo & Associates designed the building, and it is owned by Hines, a Texas based real estate investment company. The building's continuous helix design, culminating in a chimney-like extension, was caused by",
                  "score": "76.46527"
              },
              {
                  "id": "wiki:12022593",
                  "title": "750 7th Avenue",
                  "text": "750 7th Avenue 750 Seventh Avenue is a 615 ft (187m) tall Class-A office skyscraper in New York City. It was completed in 1989 in the postmodern style and has 36 floors. Kevin Roche John Dinkeloo & Associates designed the building, and it is owned by Hines, a Texas based real estate investment company. The building's continuous helix design, culminating in a chimney-like extension, was caused by the New York City Building Code, which requires setbacks. The 84 exterior column transfers exist because of the owner's requirement for a column-free space. It is tied with the New York Life Building",
                  "score": "76.2616"
              }
          ]
      }
  ]
  ```

这个数据集里问题的答案是通过**多跳推理**（multi-hop reasoning）从多个参考文档中找出来的。多跳推理是一种需要从不同来源逐步获得信息并进行整合的过程。我们来看这个例子：

**问题：** Were Scott Derrickson and Ed Wood of the same nationality?

1. **问题的要求**：判断Scott Derrickson和Ed Wood是否属于同一个国籍。这需要了解他们各自的国籍。
2. **提供的文档**：这里列出的文档内容并不直接提供Scott Derrickson和Ed Wood的国籍信息，但我们仍然可以使用它们的结构或与国籍相关的部分进行推理。
3. **多跳推理**：

   - **第一个跳跃**：系统需要找到Scott Derrickson的国籍。虽然提供的文档并没有直接给出Scott Derrickson的信息，但可以通过在知识库（如Wikipedia）中的相关内容找到他的国籍。Scott Derrickson是美国人。
   - **第二个跳跃**：然后，系统需要找到Ed Wood的国籍。同样，通过查阅知识库中的Ed Wood条目，可以得知他也是美国人。
4. **最终答案**：两者的国籍都是美国，因此答案是“**Yes**”。

**多跳推理的作用**是，当答案涉及多个实体（如Scott Derrickson和Ed Wood）时，系统会依次从多个文档中提取相关信息，将它们组合起来，形成完整的推理链条，从而得出结论。

### 4. **NQ (Natural Questions)**

- **类型**: 开放域问答数据集（ODQA)，extracion
- **评价标准：** EM
- **描述**: Natural Questions 是谷歌发布的问答数据集，问题来自真实的 Google 搜索查询，答案通常嵌入在维基百科文档中。任务是从提供的文档中找到问题的答案。
- **应用场景**: 用于开放域问答和长文档中的信息检索。

  ```json
      {
          "question": "who did america fight during world war 1",
          "answers": [
              "the Austro-Hungarian Empire",
              "Germany"
          ],
          "ctxs": [
              {
                  "id": "14138898",
                  "title": "United States in World War I",
                  "text": "United States in World War I The United States declared war on Germany on April 6, 1917, more than two and a half years after World War I started. A ceasefire and Armistice was declared on November 11, 1918. Before entering the war, the U.S. had remained neutral, though it had been an important supplier to Great Britain and the other Allied powers. The U.S. made its major contributions in terms of supplies, raw material and money, starting in 1917. American soldiers under General of the Armies John Pershing, Commander-in-Chief of the American Expeditionary Force (AEF), arrived at the rate"
              },
              {
                  "id": "14138937",
                  "title": "United States in World War I",
                  "text": "Republican Warren G. Harding. Notes References United States in World War I The United States declared war on Germany on April 6, 1917, more than two and a half years after World War I started. A ceasefire and Armistice was declared on November 11, 1918. Before entering the war, the U.S. had remained neutral, though it had been an important supplier to Great Britain and the other Allied powers. The U.S. made its major contributions in terms of supplies, raw material and money, starting in 1917. American soldiers under General of the Armies John Pershing, Commander-in-Chief of the American Expeditionary"
              },
              {
                  "id": "14138904",
                  "title": "United States in World War I",
                  "text": "just as German U-boats started sinking American merchant ships in the North Atlantic. Wilson then asked Congress for \"a war to end all wars\" that would \"make the world safe for democracy\", and Congress voted to declare war on Germany on April 6, 1917. On December 7, 1917, the U.S. declared war on Austria-Hungary. U.S. troops began arriving on the Western Front in large numbers in 1918. After the war began in 1914, the United States proclaimed a policy of neutrality despite president Woodrow Wilson's antipathies against Germany. Early in the war, the United States started to favor the British"
              },
              {
                  "id": "7594741",
                  "title": "World War I",
                  "text": "a result of the war: the Romanovs, the Hohenzollerns, the Habsburgs, and the Ottomans. Belgium and Serbia were badly damaged, as was France, with 1.4 million soldiers dead, not counting other casualties. Germany and Russia were similarly affected. A formal state of war between the two sides persisted for another seven months, until the signing of the Treaty of Versailles with Germany on 28 June 1919. The United States Senate did not ratify the treaty despite public support for it, and did not formally end its involvement in the war until the Knox–Porter Resolution was signed on 2 July 1921"
              },
              {
                  "id": "14138931",
                  "title": "United States in World War I",
                  "text": "the war. The Boy Scouts of America helped distribute war pamphlets, helped sell war bonds, and helped to drive nationalism and support for the war. As late as 1917, the United States maintained only a small army, one which was in fact smaller than thirteen of the nations and empires already active in the war. After the passage of the Selective Service Act in 1917, it drafted 4 million men into military service. By the summer of 1918, about 2 million US soldiers had arrived in France, about half of whom eventually saw front-line service; by the Armistice of November"
              }
          ]
      }
  ```

### 5. **TQA (Textbook Question Answering)**

- **类型**: 教材问答数据集(ODQA)，span extraction
- **评价标准：** EM
- **描述**: TQA 数据集包含来自中学科学教材的图表和文本，问题要求对课文中的内容进行推理。模型需要综合多种信息源来回答问题，这使得它成为多模态理解和推理的理想数据集。
- **应用场景**: 用于教育相关的问答模型，尤其是涉及多模态推理的任务。

  ```json
      {
          "question": "The VS-300 was a type of what?",
          "answers": [
              "🚁",
              "Helicopters",
              "Civilian helicopter",
              "Pescara (helicopter)",
              "Cargo helicopter",
              "Copter",
              "Helecopter",
              "List of deadliest helicopter crashes",
              "Helichopper",
              "Helocopter",
              "Cargo Helicopter",
              "Helicopter",
              "Helicoptor",
              "Anatomy of a helicopter"
          ],
          "target": "Helicopter",
          "ctxs": [
              {
                  "id": "7108852",
                  "title": "Vought-Sikorsky VS-300",
                  "text": "Vought-Sikorsky VS-300 The Vought-Sikorsky VS-300 (or S-46) is a single-engine helicopter designed by Igor Sikorsky. It had a single three-blade rotor originally powered by a 75 horsepower (56 kW) engine. The first \"free\" flight of the VS-300 was on 13 May 1940. The VS-300 was the first successful single lifting rotor helicopter in the United States and the first successful helicopter to use a single vertical-plane tail rotor configuration for antitorque. With floats attached, it became the first practical amphibious helicopter. Igor Sikorsky's quest for a practical helicopter began in 1938, when as the Engineering Manager of the Vought-Sikorsky Division"
              },
              {
                  "id": "6173576",
                  "title": "Schweizer 300",
                  "text": "Schweizer 300 The Schweizer RSG 300 series (formerly Sikorsky S300, Hughes 300 and Schweizer 300) family of light utility helicopters was originally produced by Hughes Helicopters, as a development of the Hughes 269. Later manufactured by Schweizer Aircraft, the basic design has been in production for almost 50 years. The single, three-bladed main rotor and piston-powered S-300 is mostly used as a cost-effective platform for training and agriculture. In 1955, Hughes Tool Company's Aircraft Division (later Hughes Helicopters) carried out a market survey showing that there was a demand for a low-cost, lightweight, two-seat helicopter. The division began building the"
              },
              {
                  "id": "15043580",
                  "title": "Berliner Helicopter",
                  "text": "Berliner Helicopter The Berliner Helicopters were a series of experimental helicopters built by Henry Berliner between 1922 and 1925. The helicopters had only limited controllability but were the most significant step forward in helicopter design in the USA until the production of the Vought-Sikorsky VS-300 helicopter in 1940. The 1922 flights of the Berliner and the de Bothezat H1 were the first by manned helicopters. Emile Berliner, an inventor famous for his invention of the flat gramaphone record, had experimented with intermeshing helicopters as early as 1907. The initial design was underpowered and called for a lighter engine. Berliner developed"
              },
              {
                  "id": "3591612",
                  "title": "Martell (cognac)",
                  "text": "his widow and then his two sons and grandson continued this tradition and developed the export business to make Martell the number one in England in 1814. In 1831, Martell created his first \"VSOP\" (Very Superior Old Pale) cognac and continued its international expansion. Its fame spread throughout the world, with the first exports to Japan and other Asian markets, such as Indonesia, Vietnam, Malaysia and Korea. Cordon Bleu, created in 1912, is certainly the company’s most famous product. Martell was served aboard the Queen Mary in 1936 and even on Concorde in 1977. In 1987, Seagram took control of"
              },
              {
                  "id": "20113517",
                  "title": ".300 Rook",
                  "text": "well as bullet drop over longer distances. The origins of the .300 Rook are uncertain although it was introduced before 1874, it became one of the most popular British rook cartridges, also being chambered in several revolvers. In later years its popularity was eroded by the .255 Jeffery Rook and to Holland & Holland's .297/250 Rook. The .300 Rook cartridge case was lengthened to create the .300 Sherwood, which in turn superseded the .300 Rook target variant. As with other rook rifle cartridges, the .300 Rook was superseded by the .22 Long Rifle. .300 Rook The .300 Rook, also known"
              }
          ]
      },
  ```

### 6. **WoW (Wizard of Wikipedia)**

- **类型**: 对话生成数据集。  generate
- **数据：** In each example, the input q is the conversation history involving multiple utterance turns, and the next-turn response is the output o.
- **评价标准：** unigram F1-score
- **描述**: WoW 数据集用于训练模型生成具有丰富知识的对话。它包含基于维基百科知识的开放域对话，模型在回答问题时需要引用背景知识，提供连贯的、信息丰富的回答。
- **应用场景**: 用于对话生成，特别是知识增强型对话系统。

  ```json
      {
          "question": "i love baking ,i bake cakes for my family every weekends\nThat's awesome! Do you bake bread too?\nyes i usually bake also bread once in a while",
          "answers": [
              "Baking bread is an ancient activity. I have only baked bread once as a 4H project as a kid"
          ],
          "ctxs": [
              {
                  "id": "wiki:2381033",
                  "title": "Bakery",
                  "text": "en Acción . Upper Saddle River, Nueva Jersey 07458: Pearson Prentice Hall. pag. 111. ISBN 0-13-063085-3 . Aliberha6573 Política de privacidad borrado de cookies Some bakeries provide services for special occasions (such as weddings, birthday parties, anniversaries, or even business events) or for people who have allergies or sensitivities to certain foods (such as nuts, peanuts, dairy or gluten). Bakeries can provide a wide range of cakes designs such as sheet cakes, layer cakes, tiered cakes, and wedding cakes. Other bakeries may specialize in traditional or hand made types of bread made with locally milled flour, without flour bleaching agents",
                  "score": "82.39265",
                  "has_answer": false
              },
              {
                  "id": "wiki:17051727",
                  "title": "Semifreddi's Bakery",
                  "text": "two major players in the San Francisco Bay bread industry. In 2009, Semifreddi’s moved into a 33,000 square foot facility, where the bakery recycles 95 percent of its waste. It operates 24 hours a day, 7 days a week, for all 52 weeks of the year. The bakery utilizes over 25 different recipes and bakes more than 50 different artisan breads and pastries. In a typical week, Semifreddi’s bakes and delivers over 200,000 baguettes, rolls, and loaves and 40,000 pastries and cookies a week. Semifreddi’s sells to grocery stores, restaurants, and cafés throughout the bay area. Semifreddi’s bakes French and",
                  "score": "80.79461",
                  "has_answer": false
              },
              {
                  "id": "wiki:16552238",
                  "title": "Jeff Hertzberg",
                  "text": "Press/Macmillan Publishers, has published all of their books. Artisan Bread in Five Minutes a Day was an instant success upon its publication in 2007, earning coverage on the Today Show, in the New York Times and the Chicago Tribune, as well as other publications. Hertzberg and François have written two follow-up books: Healthy Bread in Five Minutes a Day (2009) and Artisan Pizza and Flatbreads in Five Minutes a Day (2011). The authors provide online support for readers through their blog. Jeff Hertzberg Jeff Hertzberg is an American cookbook author and a physician. With co-author Zoë François, he has created",
                  "score": "80.43113",
                  "has_answer": false
              },
              {
                  "id": "wiki:3947547",
                  "title": "Bread machine",
                  "text": "cake. One of the most recent innovations is the facility to add nuts and fruit during the kneading process automatically from a tray. Traditionally, breadmakers take between three and four hours to bake a loaf. However recently \"fast bake\" modes have become common additions, many of which are able to produce a loaf in under an hour. The bread is generally not of as good quality as that produced by a longer program, but for many users this is a useful feature. Most of the best bread machines have a cold wall which usually protects the surface getting hotter during",
                  "score": "80.200676",
                  "has_answer": false
              },
              {
                  "id": "wiki:11331227",
                  "title": "Veniero's",
                  "text": "added an adjoining warm enclave, with a ceiling of stained-glass panels and the original pressed tin. Frank Zerilli changed the oven from coal to gas by the 1980s as well, and more recently Veniero's began selling carb-free cheesecakes and sugar-free cookies. Veniero's is famous for its traditional and regional Italian confections, including handmade Italian butter cookies, biscotti, cannoli, sfogliatelle, tiramisù, and its New York staple cheesecake. Veniero's was featured in the first New York City episode of Food Network's \"Road Tasted\" and has been featured on many other shows, including ABC's \"Good Morning America\" and \"Live with Regis and Kelly\",",
                  "score": "79.69207",
                  "has_answer": false
              }
          ]
      }
  ```

这些数据集在 RAG 模型中通常用于训练模型理解复杂问题、进行推理、事实验证以及生成丰富、连贯的回答。

# 本文Pipeline

### **key idea**：

 对检索文档的**句子级过滤**（大模型Mctx），将过滤的句子作为上下文，结合问题预测答案（大模型Mgen）

### Method：

**主要目标**：训练Mctx，训练Mgen

**Mctx训练数据集**创建：使用三种硬方法（指有固定算法）： (i) entailment, (ii) lexical overlap, and (iii) conditional cross-mutual information (CXMI).    从文档中筛选句子，作为**目标输出**。问题和文档作为**训练输入**。

**Mgen训练数据集**创建：本文是用三种硬方法筛选出来的句子作为参考文档，结合问题一起作为**训练输入**，raw_data['answers'][best]作为**目标输出**

## Install

Install all required libraries by running

```bash
pip install -r requirements.txt
```

Retrieve top relevant Wikipedia passages using [Dense Passage Retriever (DPR)](https://github.com/facebookresearch/DPR)
and store into the `./datasets/${name}` directory. We also provide preprocessed datasets with top-5 retrieved passages [(here)](https://drive.google.com/file/d/13z_qrVOBlgu75IJBpX-1vMSCC6hC9yH4/view?usp=sharing).
We specify `${name}` for six datasets with ['nq', 'tqa', 'hotpotqa', 'fever', 'wow'] in following example commands.

## Measure Retrieved Passages（preprocess for obtain training & testing data)

Before filtering out potentially redundant context, we need to measure the utility scores of individual spans in the retrieved passages.
You can use any of the three context filtering strategies:
(i) entailment, (ii) lexical overlap, and (iii) conditional cross-mutual information (CXMI).

Use `measure_ctxs.py` to measure the utility score of each retrieved passage,
as well as individual sentences within, for example:

```bash
python measure_ctxs.py \
--dataset_path "./datasets/eli5/base/train.json" \
--output_path  "./datasets/eli5/scored/train.json" \
--metric_name  "strinc" "lexical" "cxmi" \
--n_contexts 5 \
--prefix "Given the ['context', 'question'], predict the answer to the question:"
```

If "cxmi" is specified as one of the `metric_name`s, make sure you specify the huggingface model to use in `model_name_or_path`. Or it will use "google/flan-t5-xl" by default.

## Obtain Training & Testing Data

Use `get_inputs.py` to create input-output training pairs for both the context filtering model $M_{ctx}$ and generation model $M_{gen}$.

The training pairs looks like

For the _context filtering task_, the input should be all top-K retrieved passages, and the output is context filtered with one of the three strategies.

```bash
python get_inputs.py \
--dataset_path "./datasets/eli5/scored/train.json" \
--output_path "./datasets/eli5/mctx/em/train_em_top1.json" \
--input_list question passage --output_list filtered \
--n_examples 0 --n_contexts 1 \
--filter_criteria strinc --print_example
```

Alter the value of `n_examples` to include more in-context examples. Adjust the value of `n_contexts` to change the number of retrieved passages involved. `filter_criteria` specifies which filtering strategy you want to use, among ['strinc', 'lexical', 'cxmi'].

The training pairs looks like

```json
[
  {
    "input": "Given the ['question', 'context'], predict the most helpful sentence in the context.\n\nquestion: In Trading Places (1983, Akroyd/Murphy) how does the scheme at the end of the movie work? Why would buying a lot of OJ at a high price ruin the Duke Brothers?\ncontext: she left, she made plans that the two children spend the vacation with their grandfather, Los Angeles billionaire J.W Osborne. Neither the children nor Osborne are enthused. Osborne, who has bad experiences with the children, takes steps to ensure the same level of chaos is not repeated. During the plane trip, Jay realizes he has mislaid his pet skunk, Duster. In the horror and panic ensuing from the loss, Osborne's loyal butler, Mr. Jamieson, fails to meet them at the airport, and the children make their escape in a taxi. Meanwhile, at the same airport, safe-crackers and robbers Duke and",
    "output": "Osborne, who has bad experiences with the children, takes steps to ensure the same level of chaos is not repeated."
  },
  {
    "input": "Given the ['question', 'context'], predict the most helpful sentence in the context.\n\nquestion: What causes the trail behind jets at high altitude?\ncontext: gaseous water cools. A distrail forms when the heat of engine exhaust evaporates the liquid water droplets in a cloud, turning them back into invisible, gaseous water vapor. Contrail Contrails (; short for \"condensation trails\") are line-shaped clouds produced by aircraft engine exhaust or changes in air pressure, typically at aircraft cruise altitudes several miles above the Earth's surface. Contrails are composed primarily of water, in the form of ice crystals. The combination of water vapor in aircraft engine exhaust and the low ambient temperatures that exist at high altitudes allows the formation of the trails. Impurities in the engine",
    "output": "Contrail Contrails (; short for \"condensation trails\") are line-shaped clouds produced by aircraft engine exhaust or changes in air pressure, typically at aircraft cruise altitudes several miles above the Earth's surface."
  },
  {
    "input": "Given the ['question', 'context'], predict the most helpful sentence in the context.\n\nquestion: babies crying pre-sedentary/having shelters if it would technically be a death sentence attracting predators in nature\ncontext: Safe-haven law Safe-haven laws (also known in some states as \"Baby Moses laws\", in reference to the religious scripture) are statutes in the United States that decriminalize the leaving of unharmed infants with statutorily designated private persons so that the child becomes a ward of the state. \"Safe-haven\" laws typically let parents remain nameless to the court, often using a numbered bracelet system as the only means of linking the baby to the parent. Some states treat safe-haven surrenders as child dependency or abandonment, with a complaint being filed for such in juvenile court. The parent either defaults or answers",
    "output": "Safe-haven law Safe-haven laws (also known in some states as \"Baby Moses laws\", in reference to the religious scripture) are statutes in the United States that decriminalize the leaving of unharmed infants with statutorily designated private persons so that the child becomes a ward of the state."
  },
  {
    "input": "Given the ['question', 'context'], predict the most helpful sentence in the context.\n\nquestion: Do animals know they're going to die?\ncontext: Animal loss The death of a pet or an animal to which one has become emotionally bonded can be an intense loss, comparable with the death of a human loved one, or even greater depending on the individual. The death can be felt more intensely when the owner has made a decision to end the pet\u2019s life through euthanasia. While there is strong evidence that animals can feel such loss for other animals, this article focuses on human feelings, when an animal is lost, dies or otherwise is departed. There is no set amount of time for the grieving process",
    "output": "Animal loss The death of a pet or an animal to which one has become emotionally bonded can be an intense loss, comparable with the death of a human loved one, or even greater depending on the individual."
  }
]
```

For the _generation task_, the input should be filtered context, and output is the annotated output.

```bash
python get_inputs.py \
--dataset_path "./datasets/eli5/scored/train.json" \
--output_path "./datasets/eli5/mgen/em/train_em_top1.json" \
--input_list question filtered --output_list answer \
--n_examples 0 --n_contexts 1 \
--filter_criteria strinc --print_example
```

The only changes to the context filtering case is the `input_list` and `output_list`, where we switched the input context to from entire passages ('passage') to filtered sentences ('filtered').

The trainning pairs looks like

```json
[
  {
    "input": "Given the ['question', 'context'], predict the answer to the question.\n\nquestion: In Trading Places (1983, Akroyd/Murphy) how does the scheme at the end of the movie work? Why would buying a lot of OJ at a high price ruin the Duke Brothers?\ncontext: she left, she made plans that the two children spend the vacation with their grandfather, Los Angeles billionaire J.W Osborne. Neither the children nor Osborne are enthused. Osborne, who has bad experiences with the children, takes steps to ensure the same level of chaos is not repeated. During the plane trip, Jay realizes he has mislaid his pet skunk, Duster. In the horror and panic ensuing from the loss, Osborne's loyal butler, Mr. Jamieson, fails to meet them at the airport, and the children make their escape in a taxi. Meanwhile, at the same airport, safe-crackers and robbers Duke and",
    "output": "answer: The final scene involves future contracts. This simply means entering into a contract to buy something (oil, wheat, even frozen concentrated orange juice(FCOJ)) at a specified time for the current price. The person selling the future does not have to own the FCOJ at the time of sale he simply has to provide them at the agreed upon date. Futures help companies mitigate risk against the unpredictable price of FCOJ. If the price of FCOJ goes up the buyer wins the seller loses and visa versa. This price is often affected by fresh oranges. If there is a good harvest FCOJ price goes down and so on. The Dukes believed there was going to be a bad harvest. Their plan was to buy as much FCOJ as they could and basically corner the market then sell it at a much higher price due to a lack of oranges. So here is what happened. At first Winthrop and Valentine begin selling futures contracts at inflated prices caused by the Dukes (on the info from the fake report of a bad orange harvest) at approximately $1.45 per unit. When the report comes out that the orange harvest is expected to be good caused a massive selloff and the futures price plummeted to about $.22 cents. This is when Winthrop and Valentine begin buying futures instead of selling. So now they can fill the futures orders of $1.45 with oranges costing $.22 earning something like a 545% profit."
  },
  {
    "input": "Given the ['question', 'context'], predict the answer to the question.\n\nquestion: What causes the trail behind jets at high altitude?\ncontext: gaseous water cools. A distrail forms when the heat of engine exhaust evaporates the liquid water droplets in a cloud, turning them back into invisible, gaseous water vapor. Contrail Contrails (; short for \"condensation trails\") are line-shaped clouds produced by aircraft engine exhaust or changes in air pressure, typically at aircraft cruise altitudes several miles above the Earth's surface. Contrails are composed primarily of water, in the form of ice crystals. The combination of water vapor in aircraft engine exhaust and the low ambient temperatures that exist at high altitudes allows the formation of the trails. Impurities in the engine",
    "output": "answer: It is water vapor and ice. They are produced from the hot engine exhaust in the cold atmosphere. Water vapor from the engine exhaust mixed with unburnt particulate in the jet fuel gives the surrounding moist air something to latch onto and ice crystals form. Depending on the hight of the aircraft, they can last seconds to hours. If you have seen a running car on a brisk morning, that is a similar effect. The car is too close to the relatively warmer ground that trails do not last for more than a second."
  },
  {
    "input": "Given the ['question', 'context'], predict the answer to the question.\n\nquestion: babies crying pre-sedentary/having shelters if it would technically be a death sentence attracting predators in nature\ncontext: Safe-haven law Safe-haven laws (also known in some states as \"Baby Moses laws\", in reference to the religious scripture) are statutes in the United States that decriminalize the leaving of unharmed infants with statutorily designated private persons so that the child becomes a ward of the state. \"Safe-haven\" laws typically let parents remain nameless to the court, often using a numbered bracelet system as the only means of linking the baby to the parent. Some states treat safe-haven surrenders as child dependency or abandonment, with a complaint being filed for such in juvenile court. The parent either defaults or answers",
    "output": "answer: Hardly. First, remember that babies were not left unattended. Our early ancestors (much like some hunter gatherer tribes still do to this day) carries their babies around constantly. Babies that are worn cry much less because pretty much their every need (food and comfort) are very close by. Additionally, we are a species that lives in groups. A group of humans is going to be loud in any situation, and the occasional baby cry is not going to add much to that. Living in a group was our protection already, not stealth."
  },
  {
    "input": "Given the ['question', 'context'], predict the answer to the question.\n\nquestion: Do animals know they're going to die?\ncontext: Animal loss The death of a pet or an animal to which one has become emotionally bonded can be an intense loss, comparable with the death of a human loved one, or even greater depending on the individual. The death can be felt more intensely when the owner has made a decision to end the pet\u2019s life through euthanasia. While there is strong evidence that animals can feel such loss for other animals, this article focuses on human feelings, when an animal is lost, dies or otherwise is departed. There is no set amount of time for the grieving process",
    "output": "answer: Animals, at least higher functioning mammals, have some sort of concept of death, though I don't know how much it differs from what you or I understand death to be. Elderly pack animals (wolves, for example) will voluntarily leave the pack, stop eating, and find a quiet place to die, for example. Elephants that come across the bones of another elephant will stop and \"feel\" skulls with their trunks and even cover remains with brush."
  },
]
```

## Training A Context Filtering Model

Perform the above processing on training, validation, and test data,
then to fine-tune a FlanT5 (xl) model using `train.py`, which passes
in "google/flan-t5-xl" to the `model_name_or_path` argument by default.

```bash
python train.py \
--train_data_path "./datasets/eli5/mctx/em/train_em_top1.json" \
--eval_data_path "./datasets/eli5/mctx/em/dev_em_top1.json" \
--test_data_path "./datasets/eli5/mctx/em/test_em_top1.json" \
--output_dir "./checkpoints/eli5-mctx_filco-em" \
--do_train --do_eval --do_predict
```

After training, load the fine-tuned checkpoint to predict filtered context for testing examples.

```bash
python query.py \
--dataset_path "./datasets/eli5/mctx/em/test_em_top1.json" \
--output_path "./output/eli5/mctx/filco-em_tuned-ft5.json" \
--model_name_or_path "./checkpoints/eli5-mctx_filco-em"
```

After this, convert the dataset to generation example format by

```bash
python replace_context.py \
--dataset_path "./datasets/eli5/base/test.json" \
--predset_path "./output/eli5/mctx/filco-em_tuned-ft5.json" \
--output_path "./datasets/eli5/mgen/em/test_em_top1_predict-ft5.json" \
--process_dataset nq
```

To train and query LLaMa models, switch the model name to "meta-llama/Llama-2-7b-hf".
Alternatively using xTuring, run `train_llama.py` and `query_llama.py` with similar arguments, but transform the examples into instruction style using `convert_dataset.py`.

## Training A Generation Model with Filtered Context

Prepare the training and validation data using the same method,
then train Flan-T5 models using `train.py` and LLaMa models with `train_llama.py`.

```bash
python train.py \
--train_data_path "./datasets/eli5/mgen/em/train_em_top1.json" \
--eval_data_path "./datasets/eli5/mgen/em/dev_em_top1.json" \
--test_data_path "./datasets/eli5/mgen/em/test_em_top1.json" \
--output_dir "./checkpoints/eli5-mgen_filco-em" \
--do_train --do_eval --do_predict
```

To use the tuned model checkpoint for inference, run

```bash
python query.py \
--dataset_path "./datasets/eli5/mgen/em/test_em_top1.json" \
--output_path "./output/eli5/mgen/silver-em_tuned-ft5.json" \
--model_name_or_path "./checkpoints/eli5-mgen_filco-em"
```

Switch the silver filtered context (e.g., "./datasets/nq/mgen/em/train_em_top1.json") to model filtered context (e.g., "./output/nq/mctx/filco-em_tuned-ft5.json") to experiment in the __FilCo__ setting.

## Evaluating Filtering and Generation Models

To evaluate the generation performance, use the EM (~Accuracy) or F1
according to the task formulation.

```bash
python eval.py \
--dataset_path "./datasets/eli5/base/test.json" \
--predset_path "./output/eli5/mgen/silver-em_tuned-ft5.json" \
--metric_name "em"
```

## Reference

If you find our paper or code useful, please cite the paper

```
@article{wang2023learning,
  title={Learning to Filter Context for Retrieval-Augmented Generation},
  author={Zhiruo Wang, Jun Araki, Zhengbao Jiang, Md Rizwan Parvez, Graham Neubig},
  journal={arXiv preprint arXiv:2311.08377},
  year={2023}
}
```
