---
layout: post
title: "Reflections on Teaching a Blockchain Seminar"
date: 2020-03-10
categories: blockchain
tags: [blockchain]
---

For the first half of this semester, up until Spring Break, I developed the material for and taught a weekly seminar formally titled "Topics in Blockchain" at Penn to a crowd of students interested in learning more about what is happening in this rapidly evolving space. The course met for a total of six sessions, with each session being about 90 minutes.

The initial idea for this course came about because of a failed attempt to organize a blockchain whitepaper presentation group the previous semester as part of the Penn Blockchain Club. Realizing it would be difficult to get a critical mass of people dedicated enough to reading and present on blockchain papers, I decided to essentially do the I had also learned so much about blockchain technology from my internship at Coinfund the previous summer, and wanted to expand and share my knowledge.

What I hoped to accomplish, in order to make the course as friendly as possible to students of all backgrounds, was to get everyone caught up on the basics of how blockchains work, and then go into a few interesting case studies of how blockchains and smart contracts could be applied to solve interesting problems and create novel economic mechanisms. I did not want the material to be highly technical, and present only the most interesting ideas from different areas of blockchain.

Here are my thoughts after each session and links to the slides that I made.

# Session 1: Introduction to Blockchain and Bitcoin

[Slides]({% link /assets/files/intro_to_blockchain.pdf %})

The first session was meant to be an introduction to how blockchains work by way of the Bitcoin protocol, and then an introduction to Ethereum and smart contracts. I greatly overestimated how much content I would be able to present, and about a few minutes in to the presentation, realized that I should just slow down and clearly explain the first half on how Bitcoin works. I ended up answering a lot of questions and doing a lot of drawing on the board, showing different cases of how

# Session 2: Ethereum and Smart Contracts

[Slides]({% link /assets/files/intro_to_blockchain.pdf %})

I started the second session with review and taking questions about Bitcoin, making sure everyone remembered how it worked. I was generally surprised how well everyone understood the basic protocol, as we quickly went through the steps of a Bitcoin block. Given that I was only able to cover Bitcoin in the first session, I spent the second session mostly going through the second half of the slides I had originally prepared, focusing on Ethereum and smart contracts. In my mind, the shift in between thinking about Bitcoin to Ethereum was a simple one: for Bitcoin, each block stores transactions whereas for Ethereum, each block stores program execution. This proved to be a bit more difficult to explain given the diverse programming and computer science background of the group, but in the end I think everyone went out with a basic understanding of how programs are executed. Much of my time this session was also spent writing on the board, drawing examples of smart contracts and transactions interacting in the network.

# Session 3: Stablecoins and Maker

[Slides]({% link /assets/files/maker_dao.pdf %})

After introducting the notion of smart contracts in Session 2, I wanted to really demonstrate the power of smart contracts by abstracting away from the technology and start a discussion on the novel game theory and economics enabled by decentralized program execution. I decided to do this through a case study of the Maker stablecoin system, and spent most of the time going into the details of how the system works. At the end, I had a few people who were still not convinced about how the collateral system was secure, despite being able to repeat back how the system works. I think this is common when it comes to thinking about complex systems, where understanding how things work mechanically doesn't give you the understanding of the system as a whole. Ultimately, I think that thinking through the cases of what could go wrong in the Maker system, such as a flash crash in ETH price or a large deviation in DAI price, is the best way to see how the system works together, and is what I tried to work through with the people who stayed after.

# Session 4: Decentralized Exchanges

[Slides]({% link /assets/files/decentralized_exchanges.pdf %})

For this session, I was hoping to continue showing the power of smart contracts and illustrate how a vibrant ecosystem of decentralized exchanges has popped up on Ethereum. I have always been fascinated by decentralized exchanges, but I never found a resource that compared and contrasted the numerous designs out there. So, I sought to understand a few of the different designs and synthesize how decentralized exchanges have evolved over time. I definitely also prepared too much material for the session, and ended up speeding through some of the slides, but the main point I was hoping to get across is the idea of how this technology is evolving and some of the basic mechanisms of automated market makers.

# Session 5: Blockchain Governance and DAOs

[Slides]({% link /assets/files/governance_and_daos.pdf %})

During my summer working at Coinfund, the co-founder, Jake Brukhman, introduced me to the fascinating topic of weighted voting with a toy Bhanzaf index example, showing how voting dynamics can be quite complicated. I was further impressed by how relevant the topic was to blockchains, as many protocols need to deal with the problem of voting in on-chain governance. The presentation for this week was inspired by that example, and also some of the articles that Jake recommended to me on blockchain governance. After covering stablecoins and decentralized exchanges, which were very case-study heavy and focused on certain implementation details, I thought that the much more broad and theoretical ideas of governance would be a good contrast. The session ended up going well, and I think the sheer number of "interesting ideas" in this session definitely blew some minds.

# Session 6: Token Distribution

[Slides]({% link /assets/files/token_distribution.pdf %})

For the final meeting, I decided to start with an hour-long presentation on token distribution mechanisms. I decided to keep the presentation short so that I could save time to do shallow-dives into some of the topics surrounding blockchains that we did not get to cover in the course, just to give an idea of the different things people are working on in the space, from theoretical developments in cryptography to applications in insurance. At the very end, I also had a low pressure pop quiz, just for fun, of the big picture ideas from the course, where I would go down the line asking everyone a question and having people jump in to help or add ideas. At the end, I was definitely somewhat sad that it was the last meeting, but it ended on a great note.

# Conclusion

Overall, this experience was extremely rewarding, as I it was a great learning opportunity for me to research topics in preparation for each session. The topics that I covered were quite focused on the Ethereum ecosystem and were heavy on decentralized finance, but I guess that was what I am most interested in and had the most motivation of researching on my own. I also had the chance to meet other Penn students of different backgrounds, from engineering students to business undergrads to MBAs, all with a shared interested in blockchain technology. The community that we built around the course was phenomenal and I hope to do this again with the club.
