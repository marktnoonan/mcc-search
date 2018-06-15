<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Sart typing a song title and we will tell you what albums contain this song:</p>
    <input type="search" v-model="searchTerm">
    <br>
    <br>
    <span v-if="numberOfResults">Found {{numberOfResults}} albums with "{{searchTerm}}" in the Track List or Description: </span>
    <albumCard :album="album" v-for="album in foundAlbums" :key="album.TITLE">
    </albumCard>
  </div>
</template>

<script>
import albumCard from "./albumCard";
export default {
  name: "HelloWorld",
  components: { albumCard },
  watch: {
    searchTerm: function(newSearch) {
      this.foundAlbums = this.albums.reduce(function(acc, current) {
        if (
          newSearch.length > 2 &&
          current.DESCRIPTION.toUpperCase().indexOf(newSearch.toUpperCase()) >
            -1 &&
          current.CATEGORIES.indexOf("CDs") > -1
        ) {
          acc.push(current);
        }
        return acc;
      }, []);
      this.numberOfResults = this.foundAlbums.length;
    }
  },
  data() {
    return {
      msg: "John McCutcheon Album Search",
      searchTerm: "",
      foundAlbums: [],
      numberOfResults: 0,
      albums: [
        {
          "PRODUCT ID": 1,
          TITLE: "Trolling For Dreams",
          DESCRIPTION: "John's most recent album.",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p1_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 3,
          TITLE: "Joe Hill's Last Will - Play DVD",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The scene is 4AM, November 19, 1915. Legendary labor songwriter, Joe Hill, is in his cell at the Utah State Prison, hours away from his execution for a trumped-up murder charge. A reporter has been sent from a local paper to record his last words. Maybe Hill will give them to him, maybe he wonÃ¢ÂÂt. But first, the reporter will have to hear the story of HillÃ¢ÂÂs life, the history and thinking behind his songs, the philosophy of the Industrial Workers of the World for whom Hill writes, his thinking on life and labor, love and death. And heÃ¢ÂÂll have to hear many songs.</p><p style="color:rgb(0, 0, 0)">The scene is November 19, 2015, Salt Lake City. 100 years to the day after HillÃ¢ÂÂs execution. Legendary labor songwriter, John McCutcheon, is performing a play, written by legendary labor songwriter, Si Kahn, about those final two hours. McCutcheon breathes new life into HillÃ¢ÂÂs music, offering a startling acting debut as Hill himself, still thinking, writing, fighting about worker rights, immigration, income inequity, love, war, and solidarity.</p><p style="color:rgb(0, 0, 0)">Scene: Joe HillÃ¢ÂÂs cell in the Utah State Prison in Salt Lake City<br>Time: November 19, 1915, 90 minutes before dawn<br>ACT I<br>1) The Rebel Girl<br>2) What A Friend We Have in Jesus (by Charles Crozat Converse &amp; Joseph M. Scriven)/ Dump the Bosses Off Your Back (words by John Brill)<br>3) Hallelujah IÃ¢ÂÂm A Bum (original hymn by William Paton Mackay, words by unknown IWW member)<br>4) There Is Power in a Union<br>5) What We Want<br>6) Where the Fraser River Flows<br>7) The Wearing of the Green/Overalls and Snuff/Put Ã¢ÂÂEm on the Bum<br>8) The Preacher and the Slave<br>9) Mr. Block<br>10) The Wooden Shoe/Ta-Ra-Ra-Boom-De-Ay!<br>11) Casey Jones<br>Act II<br>12) Stung Right<br>13) Stung Right (reprise)<br>14) The Rebel Girl (reprise)<br>15) The WorkersÃ¢ÂÂ Commonwealth<br>16) There Is Power in a Union (reprise)<br>17) Tramp, Tramp, Tramp<br>18) Joe HillÃ¢ÂÂs Last Will<br>BONUS TRACKS<br>19) Dawn vigil, March 19, 2015, at the site of Joe HillÃ¢ÂÂs execution, Salt Lake City, UT.</p><p style="color:rgb(0, 0, 0)">(All songs and poems by Joe Hill except as noted, except Ã¢ÂÂJoe HillÃ¢ÂÂs Last WillÃ¢ÂÂ words by Joe Hill, music by John McCutcheon)<br>Book by Si Kahn, ÃÂ©Joe Hill Music<br>All musical arrangements by John McCutcheon ÃÂ©Appalsongs (ASCAP)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p3_i1_w166.jpeg",
          CATEGORIES: "DVDs"
        },
        {
          "PRODUCT ID": 4,
          TITLE: "Joe Hill's Last Will - CD",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Joe Hill was a songwriter for the Industrial Workers of the World, the Wobblies, back in the early 20th century. He was the ultimate utilitarian songwriter, composing pieces to be used at meetings and picket lines and rallies. He wrote songs to be sung and to be used. To be useful. His songs "The Preacher &amp; the Slave" and "Casey Jones, the Union Scab" are what some people know of his work. But veteran folk musician and longtime labor activist, John McCutcheon, has released an album bringing Joe Hill\'s music to a whole new audience. With fresh arrangements, stunning musicianship, and released on a palette that makes these songs feel as though they were written today rather than a century ago, there is a life and vitality that is both rare and refreshing.</p><p style="color:rgb(0, 0, 0)">Joe Hill was executed by a Utah firing squad at dawn, November 19, 1915. This album is being released in honor of the centenary of Hill\'s death.</p><p style="color:rgb(0, 0, 0)">Casey Jones<br>ItÃ¢ÂÂs a Long Way Down to the Soup Line<br>The Tramp<br>Joe HillÃ¢ÂÂs Last Will<br>Mr. Block<br>What We Want<br>The Preacher &amp; the Slave<br>Overalls &amp; Snuff/The ConnaughtmanÃ¢ÂÂs Rambles<br>The Wooden Shoe/Ta Ra Ra Boom De Ay<br>The Rebel Girl<br>Stung Right<br>Where the Fraser River Flows<br>There Is Power in a Union</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p4_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 5,
          TITLE: "22 Days",
          DESCRIPTION:
            '<br>22 Days began as an homage to my friend, Vedran Smailovic, the Ã¢ÂÂCellist of Sarajevo,Ã¢ÂÂ who, in honor of 22 people killed by a bomb in a Bosnian breadline, played for 22 days in a row at the bombing site. 20 years to the day of the beginning of SmailovicÃ¢ÂÂs action I sat down for the same number of days, at the same hour every day, to write. There was no goal, no album in sight. I simply wanted to write and see what happened. Over 30 new songs is what happened. With a couple of exceptions, it is songs from that writing intensive that comprise the songs of 22 Days.<br><br>Some songs have been heard, as theyÃ¢ÂÂve been finished, in concerts throughout the past year. Those of you in the Song of the Month Club have heard one each monthÃ¢ÂÂ¦and, in fact, helped hone them with me. And they are a diverse lot: several love songs, a song about a small South Georgia town, a topical song or two, an instrumental, a hillbilly sea shanty, and a even a kind of follow-up to the Ode to a Krispy Kreme from the Passage album a few years ago.<br><br>Some of the songs I recorded in my studio here in Georgia, some overdubs with pals in Nashville, and all the vocals and mixing done back at Bias Studios up in Virginia, where I recorded for over 25 years.<br><br>Forgotten<br>Fitzgerald<br>Of an Age<br>HeavenÃ¢ÂÂs Kitchen<br>Morning<br>Dry Land Fish<br>Nothing Like You<br>OrionÃ¢ÂÂs Belt<br>The Night That Dan Ryan Got Locked in the Pub<br>Tonight<br>She Sings<br>The Man Walking His Dog<br>Adagio in AmÃ¢ÂÂ<br><br>Year released:<span style="color:rgb(0, 0, 0)">&nbsp;</span><span style="color:rgb(0, 0, 0)">2013</span><br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p5_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 6,
          TITLE: "Hammer Dulcimer Instruction - DVD",
          DESCRIPTION:
            '<div>YouÃ¢ÂÂll learn how to tune and set up your instrument, hold the hammers, find all the notes and chords, play scales, build coordination between your right and left hands and develop rolls, flams and other special hammering techniques. Tunes include: "Golden Slippers," "Liberty," "Skip to My Lou," "Lonesome John," "FisherÃ¢ÂÂs Hornpipe," "ScullyÃ¢ÂÂs Reel" and "Planxty Fanny Power."</div>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p6_i1_w156.jpeg",
          CATEGORIES: "DVDs, Instruction"
        },
        {
          "PRODUCT ID": 7,
          TITLE: "Songwriting Lessons - Single Lesson",
          DESCRIPTION:
            "John is now offering private one-on-one video songwriting lessons via Skype. Work on one of your songs in an intimate session with this award-winning, internationally-reknowned songwriter.",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p7_i1_w240.jpeg",
          CATEGORIES: "Instruction"
        },
        {
          "PRODUCT ID": 8,
          TITLE: "Songwriting Lessons - 4 Lessons",
          DESCRIPTION:
            'John is now offering private one-on-one video songwriting lessons via Skype. Work on one of your songs in an intimate session with this award-winning, internationally-reknowned songwriter.<br><span></span><strong>BEFORE YOU START</strong><br>*You have to have Skype on your computer and a Skype user name. DonÃ¢ÂÂt worry, itÃ¢ÂÂs a free program. Check out:&nbsp;<a href="http://www.skype.com/intl/en-us/home">http://www.skype.com/intl/en-us/home</a><br>*You have to have video capability (i.e. a camera built into or plugged into your computer).<br>*Have at least one work-in-progress, in written and mp3 form, that you are able to email to John. He will let you know when and how to send it. neÃ¢ÂÂll want it before your lesson.<br>*This is not a co-writing session. YouÃ¢ÂÂll be working on your song(s).<br>*The better prepared and organized you are, the more can be accomplished.<br><span></span><strong>TO GET STARTED</strong><br>*Go to the Contact section of this site (<a href="http://www.folkmusic.com/contact">http://www.folkmusic.com/contact</a>). In the Subject Line put Ã¢ÂÂSongwriting LessonÃ¢ÂÂ. Select Lessons from the Category field. Send an message to the site with your name, phone, and email and a general description of when youÃ¢ÂÂd like to arrange your lesson. Lessons will be scheduled to suit both your and JohnÃ¢ÂÂs schedules.<br>*Each lesson is 45 minutes long. It will be a private, one-on-one session with John. You may record and/or video your lesson. Check out:&nbsp;<a href="http://www.ecamm.com/mac/callrecorder/">http://www.ecamm.com/mac/callrecorder/</a><br><span></span><strong>COST AND A DEAL</strong><br>*The cost for each lesson is $95, $350 for a package of 4 lessons.<br><span></span>HereÃ¢ÂÂs a wonderful opportunity to give something unique and useful to the aspiring songwriter in your life. There will be a limit on how many John is able to do each month, so itÃ¢ÂÂs first-come-first served.<br><span></span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p8_i2_w240.jpeg",
          CATEGORIES: "Instruction"
        },
        {
          "PRODUCT ID": 9,
          TITLE: "This Land: Woody Guthrie's America",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The long-awaited all-Woody Guthrie by John McCutcheon, "This Land: Woody Guthrie\'s America" is slated for a September 15th release here at folkmusic.com. The public release is a month later. It is hailed as one of the most comprehensive and stunning tributes to this American icon. Not only is there an all-star version of "This Land Is Your" (featuring Willie Nelson, among others), but beautiful versions of Guthrie songs, classic and unknown. Joined by a cadre of the finest Americana musicians (Kathy Mattea, Tim O\'Brien, Stuart Duncan, Tommy Emmanuel), John demonstrates not only his superb musicianship, but his understanding of the legacy he is not only celebrating but continuing.</p><p style="color:rgb(0, 0, 0)">Biggest Thing that Man Has Ever Done<br>Mail Myself to You<br>I Ain\'t Got No Home<br>Deportees<br>Harness Up the Day<br>Howjadoo<br>This Morning I Was Born Again<br>Pastures of Plenty<br>1913 Massacre<br>Pretty Boy Floyd<br>Old Cap Moore<br>Ludlow Massacre<br>This Is Our Country Here<br>This Land Is Your Land<br>Hobo\'s Lullaby</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p9_i1_w200.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 11,
          TITLE: "JOHN MCCUTCHEON'S FOUR SEASONS: THE UN-BOXED SET",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">From the very beginning, John McCutcheon\'s Four Seasons was going to end up a boxed set. When each of the seasons became Grammy finalists...a first for every element in a boxed set...it seemed even more inevitable. Then Concord Music Group bought Rounder Records and the project when the way of all the best-intentioned plans. In honor of the 20th anniversary of the recording of the first installment, Summersongs, Appalseed is putting together another first: an Un-Boxed Set. All four of the Four Season sold together.</p><p style="color:rgb(0, 0, 0)">John and his co-writer, Si Kahn, have created a full year\'s worth of incredible songs, stunningly performed by a seasoned band of John\'s mates, and given us anthems to swimming holes and rivers on which to ice skate forever. Let\'s watch the Perseid Meteor shower and then the Northern Lights. How \'bout the angst of being the new kid in school come September and then suffering from Spring Fever mere months later.</p><p style="color:rgb(0, 0, 0)">This collection is a classic in children and family music, honored by the American Library Association, Parents Magazine, Parents Choice Awards, and many more...and, of course, the Grammys.</p>Ã¢ÂÂ<br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p11_i1_w237.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 15,
          TITLE: "Passage",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">With his astonishing 34th recording, Passage, folk music stalwart John McCutcheon comes full-circle. He joyously returns to many of the Appalachian sounds and themes that marked the music he played and loved music when he first came into international prominence. With a core band featuring mandolin ace Tim OÃ¢ÂÂBrien, fiddler Stuart Duncan, and bassist Bryn Davies, McCutcheon adds his own vocal, fiddle, banjo, octave mandolin, hammer dulcimer, guitar, piano, jaw harp, and harmonium skills. Singers Kathy Mattea, Suzy Bogguss, and Mollie O\'Brien round out the singing duties. But at the center of this all-star cast of musicians are the songs themselves. Rich, diverse, rooted, moving.</p><p style="color:rgb(0, 0, 0)">Pointedly contemporary, the opening cut, One More Day, is written from the perspective of one of the surviving miners in the Massey explosion in Montcoal, WV just this past spring. End of the World is the story of a Vietnamese-American shrimp boat captain in the immediate aftermath of the Gulf oil spill. Las Damas de Blanco tells of CubaÃ¢ÂÂs La-dies in White who march in protest of their sons, husbands, and fathers held as political prisoners. Your Age is a recollection of conversations with many older coal miners. Glory Halleluiah is an old-time string band rave-up with Tim and John adding increas-ingly wacky instrumentation that would have made Mike Seeger proud. Tallahassee Waltz is a gorgeous duet with Suzy Bogguss that will send many a couple out on the dance floor. And Ode to a Krispy Kreme is one of the most hilarious and spot-on spoken word narratives youÃ¢ÂÂre likely to hear.</p><p style="color:rgb(0, 0, 0)">But the Passage in the album is also personal. Father Forgive is the story of JohnÃ¢ÂÂs great-grandfather, Michael Abts, immigrating to America. Along Came You is a gift to his first grandchild. Iowa and With My Father both talk of his fatherÃ¢ÂÂs struggle with AlzheimerÃ¢ÂÂs. You CanÃ¢ÂÂt Take It with You was written after one of JohnÃ¢ÂÂs best friends died suddenly. And the albumÃ¢ÂÂs closer, Come Home, is a tribute to one of JohnÃ¢ÂÂs men-tors, the WV ballad singer and union activist, Nimrod Workman.</p><p style="color:rgb(0, 0, 0)">John McCutcheon is one of the most prolific, dependable, and entertaining musicians working today. Ã¢ÂÂThe perfect example of a modern folksinger,Ã¢ÂÂ is Sing Out! MagazineÃ¢ÂÂs description. Ã¢ÂÂA national treasure!Ã¢ÂÂ heralded the Oakland Tribute. And for nearly forty years, continuing to create music that marks our lives and our time here.</p><p style="color:rgb(0, 0, 0)">One More Day (McCutcheon) 4:02<br>End of the World (McCutcheon) 3:51<br>With My Father (McCutcheon) 2:53<br>Tallahassee Waltz (McCutcheon) 3:53<br>Father Forgive (McCutcheon) 5:14<br>You CanÃ¢ÂÂt Take It With You (McCutcheon) 3:27<br>Glory Halleluiah (McCutcheon) 3:41<br>Ode to a Krispy Kreme (McCutcheon) 3:01<br>Along Came (McCutcheon) You 3:28<br>Las Damas de Blanco (McCutcheon) 4:05<br>Friendly Competition (McCutcheon) 3:12<br>Iowa (McCutcheon) 3:20<br>Your Age (McCutcheon) 3:16<br>Come Home: (McCutcheon &amp; Si Kahn) 4:28</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p15_i1_w225.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 16,
          TITLE: "Guardabaranco: Antologia",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">This incredibly beautiful album is near the very top of JohnÃ¢ÂÂs Desert Island Disc List. Guardabaranco is the brother-sister duo, Salvador &amp; Katia Cardenal, two of NicaraguaÃ¢ÂÂs most loved singers. John met them at the Vancouver Folk Festival in 1984 and they have been fast friends since, playing together in both the US and in Nicaragua. This album is, as the title suggests, an anthology of some of the best work. It highlights SalvadorÃ¢ÂÂs masterful songwriting, KatiaÃ¢ÂÂs angelic singing, and the kind of symbiosis that can only happen when siblings sing together.</p><p style="color:rgb(0, 0, 0)">Sadly, Salvador passed away this past year after a long illness. Appalsongs has pledged to keep this recording available to the public as long as the family desires. This is currently the only on-line source for this rare and beautiful album.</p><p style="color:rgb(0, 0, 0)">Si Buscabas 2:29<br>Smaragdos Margara 2:59<br>Luna 2:10<br>Guerrero Del Amor 3:44<br>Colibri 2:58<br>Corazon De Nino 3:12<br>Disco Del Sol 4:25<br>Aunque No Fuera Para Mi 1:59<br>Dias De Amar 3:35<br>Mi Luna 4:27<br>Casa Abierta 4:43<br>Dame Tu Corazon 4:37<br>Dale Una Luz 4:37<br>Soy Latino 4:05</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p16_i1_w239.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 17,
          TITLE: "Untold (Double CD)",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">This special double-CD release is the first recording that shows the breadth of John McCutcheon\'s gifts. "Untold" features one disk that was recorded live at the 2008 National Storytelling Festival. It is the first in-depth exploration of John\'s prodigious gift as a storyteller. The second disk features three refugees from the soon-to-be out-of-print "Stand Up" and "Hail to the Chief" and a wealth of new songs audiences have heard in concert the past year. Of special note is a re-recording of "Streets of Sarajevo" with accompaniment by Vedran Smailovic, the Cellist of Sarajevo, a beautiful duet with Suzy Bogguss on John\'s "Old People in Love, " and the much-requested "Sara Tucholsky."<br><br>SONGS:<br>Long, Long Road to Home/<br>Sara Tucholsky/<br>Forget About/<br>Old People in Love (with Suzy Bogguss)/<br>Streets of Sarajevo (with Vedran Smailovic)/<br>Boys in Green/<br>El PerdÃÂ³n/<br>Different/<br>Dreams &amp; Bones/<br>Daddy Did/<br>At the Moment/<br>Prodigal Father<br><br>STORIES:<br>Survivor-Well May the World Go/<br>Sydney-Joe Hill/<br>John Henry/<br>Robbery-Forgive Us/<br>Miracle-Step by Step</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p17_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 18,
          TITLE: "Sermon On the Mound",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">"Some people say there are better games than baseball. They are wrong."<br>--Tom Boswell, The Washington Post<br><br>"The first thing in my life I ever did right," muses John McCutcheon, "was baseball." Since that day in 1959 when the lanky seven-year-old showed up a year too early for Little League tryouts (they took him anyway) McCutcheon has done quite a few other things right. With over thirty-five years of international concert touring, six Grammy nominations, countless awards, over thirty recordings and numerous books under his belt, he\'s been a busy man. With the release of Sermon on the Mound he\'s finally brought together two lifelong loves: music and baseball.<br><br>Whether honoring the games heroes (Roberto Clemente, Cal Ripkin Jr., Jackie Robinson, PeeWee Reese), tackling the game\'s foul balls (steroids, John Rocker), celebrating street ball and Little League, or distilling it all down to its essence (the universal and heart-rending \'Catch\'), once again, McCutcheon\'s pen and eye are wise, bittersweet, and wickedly funny. A home run of an album!<br><br>Sermon on the Mound (4:17)<br>Baseball on the Block (5:43)<br>Big (3:51)<br>Doing My Job (4:03)<br>Cross That Line (4:57)<br>One More Mountaintop (4:22)<br>Te Recuerdo (4:27)<br>Catch (3:55)<br>The Star Spangled Banner (1:30)<br>I Am Here (4:41)<br>Talking Yogi Talk (2:37)<br>Take Me Out to the Ballgame (0:41)<br>World Series Ã¢ÂÂ57 (3:35)<br>John Rocker (2:58)<br>Modern Kid Blues (4:30)<br>Hope I Make It (4:19)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p18_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 19,
          TITLE: "This Fire",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">People who have sat in little dark rooms with me for 35 years-worth of concerts now go on a piece of that same ride. When we gather Ã¢ÂÂround that fire thereÃ¢ÂÂs no telling what stories might be told. Songs of love and politics, courage and forgiveness, parody and pathos, somehow they are not unrelated.<br><br>When I gathered the songs for this collection they captured a small piece of time in a long life of trying hard to pay attention. They seemed to remind me of some small truths IÃ¢ÂÂve learned. If hard times canÃ¢ÂÂt have humor we wonÃ¢ÂÂt survive them. If old love doesnÃ¢ÂÂt have some memory of youthful passion it, too, will fade. And the many stories of ordinary people responding to ugliness with beauty continue to fascinate and thrill me.<br><br>Politics, love and other small miraclesÃ¢ÂÂ¦all fueled by this same fire.<br><br>Hope Dies Last (John McCutcheon) 4:56<br>Not Me (John McCutcheon) 3:30<br>Simple Man (John McCutcheon) 4:43<br>FiddlerÃ¢ÂÂs Last Dance (John McCutcheon &amp; Paul Reisler) 4:19<br>Dick Cheney (John McCutcheon) 2:08<br>Waiting for a Miracle (John McCutcheon) 4:39<br>Forgive Us (John McCutcheon) 4:13<br>SuAnne Big Crow (John McCutcheon) 3:51<br>Waist Deep in the Big Muddy (Pete Seeger) 3:17<br>Oprah Seat (John McCutcheon) 4:00<br>Twenty Todays Ago (John McCutcheon) 3:42<br>Drive All Night (John McCutcheon) 4:48<br>Boob on Our TV (John McCutcheon) 2:30<br>The Other Side (John McCutcheon) 4:06<br>This Fire (John McCutcheon) 3:47</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p19_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 20,
          TITLE: "Mightier Than The Sword",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">With his twenty-ninth album, multiple Grammy nominee John McCutcheon continues to forge new ground. Long considered one of folk musicÃ¢ÂÂs most literate songwriters, John gathers co-writers from among literatureÃ¢ÂÂs most celebrated contemporary authors: Barbara Kingsolver, Lee Smith, Wendell Berry, former US Poet Laureate Rita Dove, childrenÃ¢ÂÂs author Carmen Agra Deedy, and Dead Man WalkingÃ¢ÂÂs Sr. Helen Prejean. Drawing from history as well, this recording also features two newly discovered and completed Woody Guthrie songs and musical arrangements of poems by Nobel Laureate Pablo Neruda and CubaÃ¢ÂÂs national poet, Jose Marti. The intimate settings of these fourteen songs, the depth of the material and the breadth of subject matter are further proof of the mastery of this ever-inventive and always satisfying artist.</p><p style="color:rgb(0, 0, 0)">Our Flag Was Still There (Barbara Kingsolver/John McCutcheon)<br>La Mujer de Don Miguel (Carmen Agra Deedy/John McCutcheon)<br>Claudette Colvin Goes to Work (Rita Dove/John McCutcheon)<br>Good Old Girls (John McCutcheon, inspired by Lee Smith)<br>Dead Man Walking (John McCutcheon, inspired by Sr. Helen PrejeanÃ¢ÂÂs Dead Man Walking)<br>Cultivo Una Rosa Blanca (Jose MartÃÂ­ /John McCutcheon)<br>Harness Up the Day (Woody Guthrie/John McCutcheon)<br>Single Girl (Lee Smith/John McCutcheon)<br>Sail Away (John McCutcheon, inspired by Carmen Agra DeedyÃ¢ÂÂs Yellow Star)<br>Old Cap Moore (Woody Guthrie/John McCutcheon)<br>Para MÃÂ­ CorazÃÂ³n Basta TÃÂº Pecho (Pablo Neruda/John McCutcheon)<br>ItÃ¢ÂÂs the Economy, Stupid (John McCutcheon, inspired by Wendell BerryÃ¢ÂÂs Jayber Crow)<br>Jayber CrowÃ¢ÂÂs Silly Song about Jesus (Wendell Berry/John McCutcheon)<br>Ode to Common Things (John McCutcheon, inspired by Pablo NerudaÃ¢ÂÂs Ode to Common Things)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p20_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 21,
          TITLE: "Stand Up!",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Following on the heels of the incredibly popular 2003 release, "Hail to the Chief," John McCutcheon delivers another batch of hard-hitting, laugh-out-loud, timely songs in "Stand Up!" From aircraft carrier landings to duct tape, from Iraq to Alaska, from sending up Pat Robertson for "praying out a contract on the Supreme Court" to honoring Vedran Smalovik\'s cello playing in the streets of Sarajevo, McCutcheon proves what an incisive eye, a wicked wit and a fierce intelligence can do with topcial songwriting. With "Hail to the Chief" he was called "...one of the very few and very best of our political songwriters." With "Stand Up!" he proves what an inspiring world we live in and what an interesting year we\'ve had.</p><p style="color:rgb(0, 0, 0)">Duct Tape 3:35<br>Boys in Green 3:13<br>Let\'s Pretend 3:28<br>We Know War 4:24<br>Black Sea 3:00<br>At the Moment 4:23<br>Different 3:02<br>Love &amp; Understanding 4:01<br>Streets of Sarajevo 4:39<br>Hey Little Ant 3:11<br>We Are Not Alone 3:11<br>The Masters 1:54<br>Laz\'rus 3:54<br>Stand Up 4:37</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p21_i1_w237.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 22,
          TITLE: "Hail to the Chief!",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Folks, John has happily "retired" the many songs he wrote during the 8 years of the previous Administration. He\'s sent them all down to Crawford, TX where they\'ll relax clearing brush for the remainder of their days. Until recently, we believed this was completely out of print, but a small number turned up in a recent office move, so it\'s back for now! And this time, when they\'re gone, they\'re gone. Download is also available from the Audio Download page.<br><br>Be one of the last people to actually have recordings of "Ashcroft\'s Army," "Let\'s Pretend," "Talking Pat and Jerry Blues," "The List," and the classic, "Hail to the Chief."<br><br>And never fear! John realizes that some of the songs on each of these albums have a longer shelf-life than 43. So a new album, gathering the more universal of the songs into a new recording that will include many of the newer topical songs dealing with all things post-W. Stay tuned to the News section of the www site for updates.</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p22_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 23,
          TITLE: "The Greatest Story Never Told",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The energy that John McCutcheon and band bring to this powerful collection of all-new songs is amazing. Marking several milestones (his 50th birthday, 30 years in music and his first CD on a new label), the songs deliver powerfully concise observations on where weÃ¢ÂÂve been, where we are and where we are going. Blending rock colorations with acoustic sensibilities, this project has a refreshing and cohesive integrity. TIM OÃ¢ÂÂBRIEN and Australian KERRIANNE COX make guest appearances and JohnÃ¢ÂÂs gift for weaving astute commentary with crisp song writing and instrumental expertise is manifest through out the CD.<br><br>Greatest Story Never Told&nbsp;&nbsp; &nbsp;4:14<br>Ghosts of the Good Old Days&nbsp;&nbsp; &nbsp;3:05<br>Dancing in the Street&nbsp;&nbsp; &nbsp;5:01<br>Last First Kiss&nbsp;&nbsp; &nbsp;3:45<br>Barbershop&nbsp;&nbsp; &nbsp;3:03<br>Children of Abraham&nbsp;&nbsp; &nbsp;3:44<br>Extend a Hand&nbsp;&nbsp; &nbsp;6:03<br>Follow the Light&nbsp;&nbsp; &nbsp;4:19<br>Not in My Name&nbsp;&nbsp; &nbsp;4:34<br>When I Grow Up&nbsp;&nbsp; &nbsp;3:15<br>Used to Be&nbsp;&nbsp; &nbsp;4:21<br>Walk on Water&nbsp;&nbsp; &nbsp;4:16<br>One in a Million&nbsp;&nbsp; &nbsp;4:14</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p23_i1_w216.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 24,
          TITLE: "Supper's on the Table ... Everybody Come In!",
          DESCRIPTION:
            "<p style=\"color:rgb(0, 0, 0)\">It is easy to miss what a profoundly influential and important folk artist John McCutcheon has been over the past three decades. He is, in fact, several of the most influential folk musicians of our time; and the giant shadows cast by the trees of his many talents can obscure the forest of his total impact on the modern folk world. McCutcheon is almost unique in his ability to straddle the many branches of the modern folk tree. He is regarded among the preeminent exponents of traditional Appalachian music, and no artist has done more to popularize the ancient and very American sounds of the hammer dulcimer. He helped revolutionize the children's music market, bringing a state-of-the-art production and compositional sophistication to the acclaimed family recordings that have earned him five Grammy nominations. He is equally esteemed as a topical songwriter; his vivid ballads of real-life triumphs and travails are as much a template to political songwriters of his generation as the songs of Woody Guthrie or Phil Ochs were to theirs. This album collects a broad sampling of John McCutcheon's recordings of the past decade, with two newly recorded tracks.<br><br>Immigrant&nbsp;&nbsp; &nbsp;4:56<br>Who'll Rock the Cradle&nbsp;&nbsp; &nbsp;4:24<br>Mending Fences&nbsp;&nbsp; &nbsp;3:37<br>Calling All the Children Home&nbsp;&nbsp; &nbsp;3:22<br>Labor Day&nbsp;&nbsp; &nbsp;3:55<br>Dead Man Walking&nbsp;&nbsp; &nbsp;4:40<br>Leviathan&nbsp;&nbsp; &nbsp;4:12<br>The Principle&nbsp;&nbsp; &nbsp;2:45<br>At the Top of the Stair&nbsp;&nbsp; &nbsp;4:28<br>Jericho&nbsp;&nbsp; &nbsp;4:40<br>Snow in April&nbsp;&nbsp; &nbsp;4:28<br>Memory of Old Jack&nbsp;&nbsp; &nbsp;4:30<br>Happy Adoption Day&nbsp;&nbsp; &nbsp;3:45<br>Soup&nbsp;&nbsp; &nbsp;4:48<br>Closing the Bookstore&nbsp;&nbsp; &nbsp;4:11<br>Meteors/The Perseid&nbsp;&nbsp; &nbsp;3:56<br>Starlight&nbsp;&nbsp; &nbsp;4:58</p>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p24_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 25,
          TITLE: "Storied Ground",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Few contemporary singer-songwriters have written as passionately and consistently of the everyday struggles of working people as John McCutcheon. The Georgia-based activist remains engaged in the communities he sings about. On his 24th album he documents the perils of miners "living their lives in a two-foot seam," decries the loss of small businesses, skewers a consumerist culture "trying to make us buy what we don\'t want," and celebrates the dignity and heroism of Jackie Robinson and teammate PeeWee Reese. He performs his songs with Spartan reserve, focusing on T.J. Johnson\'s pert mandolin and J.T. Brown\'s melodic bass, though he sometimes breaks into caroming folk rock. McCutcheon is a wonderful singer and an underrated guitarist (his fingerstyle work is neat and masterful). But what sets him apart is a musical vision that remains humane, realistic, and unapologetically hopeful.</p><p style="color:rgb(0, 0, 0)">Jericho (John McCutcheon)<br>Vultures (John McCutcheon)<br>Cross That Line (John McCutcheon)<br>Key to the City (John McCutcheon &amp; Paul Reisler)<br>Homecoming Time (John McCutcheon)<br>Two Foot Seam (John McCutcheon)<br>From Us (John McCutcheon)<br>Closing the Bookstore (John McCutcheon)<br>Crazy or Courageous (John McCutcheon)<br>One More Mountaintop (John McCutcheon)<br>The Abby D (John McCutcheon)<br>Piece by Piece (John McCutcheon)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p25_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 26,
          TITLE: "John McCutcheon's Four Seasons: Springsongs",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The fourth volume in John McCutcheon\'s Four Seasons series, Springsongs completes the cycle of the seasons taking us from the melting snows of Wintersongs through to the first signs of summer, where we began the series with Summersongs. Throughout the season, we suffer from "Spring Fever," the frustration of balancing schoolwork with all of the fun which is in the airÃ¢ÂÂfishing, Little League, and just playing outside. It just isnÃ¢ÂÂt easy for a kid to keep concentrated on class work when there is so much excitement waiting just outside the classroom window.<br><br>McCutcheon cuts to the heart of the emotions that affect kids during this season. He knows how trying it is to be grounded after school when all of your friends are beckoning you to come along. The recording opens with "I Hope I Make It," expressing a childÃ¢ÂÂs desire to make the cut on the Little League team. McCutcheon evokes other seasonal highlights in "Going to the Prom," a young childÃ¢ÂÂs account of a tomboy older sisterÃ¢ÂÂs transformation for prom day; "Spring Cleaning," in which a father realizes that his childÃ¢ÂÂs accumulated junk is not too different from his own boxes in the attic; and "Snow in April," about one of those unseasonal storms which hits long after the crocuses have poked through the ground.<br><br>Throughout Springsongs (as with all of the recordings in this series) McCutcheon sees the world through a childÃ¢ÂÂs eyesÃ¢ÂÂwithout ever patronizing the child. The recording closes and the series comes full circle with "Summer is A-Coming," a rock Ã¢ÂÂnÃ¢ÂÂ roll rave up, suitable for any seasoned air guitarist.<br><br>Of course, Springsongs also features the usual high level of songwriting, musicianship, good humor, and diversity of sounds, which we have come to expect from John McCutcheon and his Four Seasons series. (Previous recordings in this series have been acclaimed for their songwriting, performance and production values, as evidenced by the fact that all four have received Grammy nominations and many other awards.)<br><br>**Grammy nominee!!<br><br>Hope I Make It (John McCutcheon &amp; Si Kahn) 4:19<br>April Fool (John McCutcheon &amp; Si Kahn) 2:29<br>Spring Fever (John McCutcheon &amp; Si Kahn) 3:52<br>Going to the Prom (John McCutcheon &amp; Si Kahn) 3:14<br>Spring Cleaning (John McCutcheon &amp; Si Kahn) 2:57<br>Snow in April (John McCutcheon &amp; Si Kahn) 3:55<br>FishinÃ¢ÂÂ (John McCutcheon &amp; Si Kahn) 2:56<br>DogÃ¢ÂÂs Life (John McCutcheon &amp; Si Kahn) 3:00<br>Grounded (John McCutcheon) 4:48<br>Junk Mail (John McCutcheon &amp; Si Kahn) 2:40<br>Frog on a Log (John McCutcheon &amp; Si Kahn) 4:11<br>Summer Is A-Coming (John McCutcheon &amp; Si Kahn) 3:52</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p26_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 27,
          TITLE: "Nothing to Lose",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">On Nothing to Lose John McCutcheon visits the lives of working men and women, small town characters and "folks who\'ve been around the block a time or two," from Alaska to Appalachia to Grenada. Seamlessly moving from folk to rock to jazz to Caribbean, McCutcheon serves up the richest musical palette of his diverse and prolific career. Whether in stark solo settings or propelled by his veteran band, McCutcheon weaves stories that are both universal and compelling, proving once again that he is ". . . a rare master at the art of the ballad." Ã¢ÂÂBoston Globe</p><p style="color:rgb(0, 0, 0)">Leftovers (John McCutcheon &amp; Si Kahn) 4:15<br>Each Season ItÃ¢ÂÂs the Same (John McCutcheon) 2:59<br>Way ItÃ¢ÂÂs Supposed to Be (John McCutcheon &amp; Si Kahn) 3:30<br>Walk On (John McCutcheon &amp; Si Kahn) 4:03<br>The Memory of Old Jack (John McCutcheon &amp; Si Kahn) 4:35<br>Nothing to Lose (John McCutcheon &amp; Si Kahn) 3:32<br>Losers Like You (John McCutcheon &amp; Si Kahn) 4:42<br>Here On the Islands (John McCutcheon) 4:30<br>Paint Me a Picture (John McCutcheon &amp; Si Kahn) 3:44<br>LeftyÃ¢ÂÂs Bar Tonight (John McCutcheon) 5:07<br>My Old Man (John McCutcheon &amp; Si Kahn) 4:30<br>Wish You Goodnight (John McCutcheon) 3:45</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p27_i2_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 29,
          TITLE: "Family Garden",
          DESCRIPTION:
            '<p>John McCutcheon is the complete modern folk musician, a master of many instruments and traditions whose own compositions have become contemporary standards. This is his third collection of songs for children and families, following his award-winning albums "Mail Myself to You" and "Howjadoo."</p><p>**1994 Notable Children\'s Recording - American Library Association<br>**1993 Parents\' Choice Award - Parents\' Choice Magazine<br>**1993 Parents Prize<br>**1993 NAPPA Silver Award.</p><p>"Rich vocals, fully realized musical arrangements and song lyrics that display gentle humor and an understanding of the interests of children make this an outstanding recording for the entire family." Ã¢ÂÂ Emergency Librarian</p><p>"Thirteen original songs vie for the status of favorite...almost an hour of pure pleasure." Ã¢ÂÂ Booklist</p><p>"McCutcheon affirms the pleasures of being together as a family, whatever the activity may be." Ã¢ÂÂ Parents Magazine</p><p>"McCutcheon\'s verse engages the dreams of children and wraps them up in music. Very meaningful and fun." Ã¢ÂÂ Childsplay</p><p>"Perhaps the best crafted children\'s album of the year." Ã¢ÂÂ Dirty Linen</p><p>Little White Star (McCutcheon)<br>Family Garden (McCutcheon/Kahn)<br>Imaginary Friend (McCutcheon/Kahn)<br>Phobias (McCutcheon/Burnley Moran 4th Grade)<br>Baseball on the Block (McCutcheon/Kahn)<br>Family Revival (McCutcheon/Kahn)<br>How Many People (McCutcheon/Kahn)<br>Traveling in the Wilderness (McCutcheon/Burnley Moran 3rd Grade)<br>Watermelon (McCutcheon/1992 CSEP)<br>Happy Adoption Day (McCutcheon)<br>Dad\'s Got That Look (McCutcheon)<br>If I Ran the World (McCutcheon/Kahn)<br>Is My Family (McCutcheon)</p><br>Year released:&nbsp;<br>&nbsp;<span>1993</span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p29_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 30,
          TITLE: "Between the Eclipse",
          DESCRIPTION:
            '<p>Between the Eclipse finds John McCutcheon in top form, immersed in the themes he knows best. From his tales of the working life to his odes to love and home, John\'s uplifting songs continue to inspire. Propelled by a band of outstanding musicians, McCutcheon displays a new energy, which prompted the Oakland Tribune to dub him "the Bruce Springsteen of folk."</p><p>"A brilliantly gifted instrumentalist and singer, McCutcheon is the kind of songwriter who thrives on concern and commitment." Ã¢ÂÂPhoenix New Times</p><p>". . . an outstanding exponent of traditional Appalachian music, who can coax deep emotions out of hammered dulcimer and autoharp. By marrying this deeply-rooted tradition with contemporary rock and country influences he forges a musical style well-suited to his message about the amazing endurance of what\'s best in American culture." Ã¢ÂÂUtne Reader</p><p>S\'posed to Do (3:47)<br>Mending Fences (3:37)<br>Dark-Haired Woman (4:10)<br>Woman Like You (4:15)<br>Old Coat (3:20)<br>Same Small Town (4:22)<br>Happened to Me (5:11)<br>She (6:26)<br>We Shall Rise (5:07)<br>Half a World Away (3:37)</p><br>Ã¢ÂÂYear released:&nbsp;<br>&nbsp;<span>1994</span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p30_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 31,
          TITLE: "Gonna Rise Again",
          DESCRIPTION:
            '<p>One of the strongest voices in folk music turns his attention to the plight of the American farmer. This album, comprised mostly of McCutcheon originals, is among his most ambitious recordings to date. A full band accompanies John on many tracks.</p><p>" . . . a master at the difficult art of the story-telling ballad. . . ." Ã¢ÂÂBoston Globe</p><p>Water from Another Time 3:12<br>Harriet Tubman 4:53<br>Long Way Back to Georgia 4:14<br>The Young Ones Don\'t Remember 5:05<br>Caught in the Crossfire 4:16<br>Satisfied Mind 5:00<br>The Farmer is the Woman 2:56<br>Dearest Martha 4:05<br>Gone Gonna Rise Again 4:13</p><br>Year released:&nbsp;<br>&nbsp;<span>1993</span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p31_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 32,
          TITLE: "Live at Wolf Trap",
          DESCRIPTION:
            "<p>Finally, a live recording of one of American folk music's most sought-after concert performers. On this recording, John McCutcheon avoids standard fare and serves up eight brand-new songs and a host of previously unrecorded favorites. Guest musicians include Tom Chapin, Paul Reisler, Pete Kennedy and others.</p><p>\". . . an appealing introduction to the newcomer and a welcome addition to the collection.\" Ã¢ÂÂHerald, CT</p><p>\"From raising kids to raising crops to raising hell, John's songs celebrate the courage, creativity and dignity of working folks. They celebrate our victories, raise our spirits, give us strength to carry on and, yes, a reason to believe.\" Ã¢ÂÂJoanne Delaplaine, Labor Heritage Foundation</p><p>Calling All the Children Home (John McCutcheon) 3:22<br>Hours After (John McCutcheon)/Lonesome John /Reel ÃÂ¡ Bouche /Leather Britches (trad.) 6:37<br>Stole &amp; Sold from Africa (trad.) 2:18<br>Black Sea (John McCutcheon) 3:00<br>Old Brown's Head Light (John McCutcheon) 4:24<br>Joe Hill (Earl Robinson &amp; Alfred Hayes) 7:23<br>Going, Going, Gone (Si Kahn) 2:33<br>High Hearts (John McCutcheon) 5:25<br>Cut the Cake (Tina Liza Jones) 6:27<br>Reasons to Believe (Tim Hardin/Bruce Springsteen) 5:03<br>Where Were You When (John McCutcheon) 3:38<br>Yesterday's Fools (John McCutcheon) 3:26<br>Christmas in the Trenches (John McCutcheon) 6:52<br>Copper River Bounce (John McCutcheon)/Money Musk (trad.) 2:38<br>The Water Is Wide (trad.) 4:50</p><br>Year released:&nbsp;<br>&nbsp;<span>1992</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p32_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 33,
          TITLE: "What It's Like",
          DESCRIPTION:
            '<p>One of the premier voices in folk music today offers a collection of original songs that explore the lives and situations of working people everywhere: the farmers, plumbers, steel workers and fishing people who are the unacknowledged backbone of society. John gets assistance from an all-star crew of musicians, including Pete Kennedy and Mary Chapin Carpenter.</p><p>"Powerful folk songsÃ¢ÂÂabout factory layoffs, lovers and landowners, union men and farming folkÃ¢ÂÂfrom John McCutcheon, the great Georgia-based troubadour." Ã¢ÂÂPhiladelphia Inquirer</p><p>"My favorite McCutcheon album" -Tommy Slothower, John\'s road manager</p><p>Cup of Coffee (McCutcheon)<br>No Turning Back Now (McCutcheon)<br>Know When to Move (McCutcheon)<br>Leviathan (McCutcheon)<br>This Time of Year (McCutcheon)<br>Ask Any Farmer (McCutcheon)<br>Stone by Stone (McCutcheon)<br>One Man\'s Trash (McCutcheon)<br>Room Here for Another (McCutcheon)<br>World Turned Upside Down (Leon Rosselson)<br>The Silver Run (McCutcheon)<br>What It\'s Like (McCutcheon)</p><br>Ã¢ÂÂYear released:&nbsp;<br>&nbsp;<span>1991</span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p33_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 34,
          TITLE: "Water From Another Time",
          DESCRIPTION:
            "<p>This 1989 collection offers a true and full retrospective of the early career of the talented folksinger John McCutcheon, drawing on his early recordings for June Appal, Front Hall, and other labels, his more recent work for Rounder, plus three previously unissued songs.</p><p>The Great Storm Is Over (Bob Franke) [4:18]<br>Little Pink (trad.) [2:28]<br>Reel ÃÂ¡ Bouche (trad.) [4:02]<br>Rubber Blubber Whale (Si Kahn) [2:48]<br>Planxty George Brabazon (Turlough O'Carolan) [2:17]<br>Christmas in the Trenches (John McCutcheon) [5:36]<br>Caught in the Crossfire (John McCutcheon) [4:01]<br>Back Side of Albany/Cooley's Reel (trad.) [3:46]<br>Wild Rose of the Mountain (Si Kahn)/Wild Rose of the Mountain (trad.) [5:00]<br>Water from Another Time (John McCutcheon) [3:09]<br>The Red Corvette (John McCutcheon) [3:30]<br>Loggerman's Breakdown (trad.)/Dulcimer Reel (Paul Van Arsdale) [3:27]<br>Cut the Cake (Tina Liza Jones) [4:12]<br>One Strong Arm (John McCutcheon) [3:54]<br>For Unto Us a Child Is Born (G.F.Handel) [3:52]<br>Featherbed (John McCutcheon) [3:06]<br>No Mas! (John McCutcheon) [3:49]<br>Step by Step (trad.) [4:12]<br>How Can I Keep from Singing? (trad.) [2:12]<br>Kindergarten Wall (John McCutcheon) [3:06]</p><br>Year released:&nbsp;<br>&nbsp;<span>1989</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p34_i1_w200.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 35,
          TITLE: "Mail Myself To You",
          DESCRIPTION:
            "<p>New versions of childhood standards are mixed with exciting new songs, played in a variety of styles, from reggae to Appalachian to Afro-Cuban. McCutcheon remains one of the most highly respected performers of children's music today.<br><br>**Notable Children's Recording - American Library<br>**Association Gold Medal Award - Parents Magazine<br>**NAIA Children's Album of the Year<br><br>\"McCutcheon is not out to prove anything, only to entertain...A fine album. A.\"Ã¢ÂÂSusan Stewart, Entertainment Weekly<br><br>\"Whether gently hammering a dulcimer on the title cut or nearly rocking out on the traditional \"Over In the Meadow,\" McCutcheon performs his second children's record with spirit and a backup band that's sensitive to the material.\" Ã¢ÂÂParents' Choice<br><br>\"The 1988 release features McCutcheon's exquisite world music arrangements and authentic instrumentation. It is the only album for children I have heard that exceeds merely quoting musical genres: it embodies them completely. McCutcheon serves up a spicy combination of South African beat, calypso, reggae, bluegrass, string band music, rock 'n' roll, new age folk-jazz, and Latin American-influenced music.\" Ã¢ÂÂAcoustic Guitar<br><br>Over in the Meadow (trad.)<br>Mail Myself to You (Woody Guthrie)<br>Barnyard Dance (Howard Armstrong)<br>Sly Little Crow (trad.)/Old Blair Store (John McCutcheon)The Awful Hilly Daddy-Willie Trip (John &amp; Will McCutcheon)<br>Teddy Bear (Widney High, Period 5)<br>New Car (Widney High, Period 5)<br>I'm a Little Cookie (Larry Penn)<br>Somos El Barco (Lorre Wyatt)<br>Hambone (trad.)<br>Kindergarten Wall (John McCutcheon)<br>Turn Around (Melvina Reynolds)<br><br>Year released:&nbsp;<br>&nbsp;1988<br></p>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p35_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 36,
          TITLE: "Signs of the Times",
          DESCRIPTION:
            '<p>This album is the first collaborative work by two of America\'s premier topical songwriters, John McCutcheon and Si Kahn. These two old friends offer insights on family and politics with an amazing breadth of humor and pathos. The original 1986 issue of this album is where modern folksong classics like McCutcheon\'s "No Mas!" and Kahn\'s "Government On Horseback" first saw the recorded light of day. On the 1994 CD reissue, each writer has contributed two new cuts, updating and maintaining the topical spirit of the original.</p><p>"Kahn and McCutcheon both contribute material, and guest artists like Pete Kennedy and Cathy Fink make this a real treat." Ã¢ÂÂAcoustic Musician</p><p>Long Time Traveling/Long Time Friends 5:11<br>Government on Horseback 2:38<br>One Thin Swimsuit 1:51<br>Welcome to the World/Willie\'s Waltz 3:46<br>By the Side of the Road * 3:07<br>Let\'s Keep It Straight* 3:44<br>One Strong Arm 3:55<br>Signs of the Times 3:15<br>No Mas 3:49<br>The Senator 2:16<br>Music in Your Hands 2:55<br>Lament 6:03<br>Featherbead 3:06<br>Friend and Companion* 3:02<br>Surprise, Surprise, Surprise* 5:05<br>Here Is My Home 3:44</p><br>Year released:&nbsp;<br>&nbsp;<span>1986</span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p36_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 37,
          TITLE: "Step by Step",
          DESCRIPTION:
            "<p>John McCutcheon's 1986 album of hammer dulcimer duets, trios, and quartets features Metamora, Trapezoid, Walt Michael and Company, and Paul Van Arsdale. Traditional instrumentals and folk songs.</p><p>\"In McCutcheon's hands the sound of the hammer dulcimer has never been more thrillingly modern!\" -Washington Post</p><p>\" . . . all of the tracks are excellent.\" Ã¢ÂÂCMJ</p><p>Reel a' Bouche 4:04<br>Santiago 4:21<br>Carolan's Welcome/Lord Inchiquin 5:04<br>Frenchie's Reel/Denver Belle 3:00<br>St. Krispajn's Cobblersguild 4:28<br>Step By Step 4:17<br>I Shall Arise 1:54<br>Robbing Peter To Pay Paul 3:13<br>Babylon Is Fallen 4:07<br>Earl Eddy's Favorite/Snowflake Breakdown 2:25<br>Derrota De Don Quixote 3:28</p><br><br>Year released:&nbsp;<br>&nbsp;<span>1986</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p37_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 38,
          TITLE: "Winter Solstice",
          DESCRIPTION:
            '<p>This classic 1984 album is McCutcheon\'s lovely set of hammer dulcimer arrangements of songs for Christmas, Chanukah and the New Year\'s Season. With help from members of the Washington Bach Consort and the group Trapezoid, John takes us on a musical journey through many lands and cultures, all in the holiday spirit. "Christmas in the Trenches" first appeared on this recording.</p><p>"The numbers featuring dulcimer and fiddle are as elegant and lovely as the sight of fresh snow on a winter\'s night." Ã¢ÂÂIsthmus</p><p>"One of the Top Ten Christmas albums of all time!" -Baltimore Sun</p><br>Year released:&nbsp;<br>&nbsp;<span>1984</span><br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p38_i1_w200.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 39,
          TITLE: "Howjadoo",
          DESCRIPTION:
            "<p>Dan Zanes said this is the album the inspired him to start playing kids' music...</p><p>John McCutcheon is a virtuoso hammer dulcimer player and a witty, incisive songwriter who has captivated audiences young and old. This album has won many awards, including the American Library Association's Recording of Notable Merit, the National Association of Independent Record Distributors' Best Children's record and a Parent's Magazine recommendation. Kids like it too! A classic in children's and family music.</p><p>\"Notable Children's RecordingÃ¢ÂÂAmerican Library Association Gold Medal Award\"Ã¢ÂÂParents Magazine</p><p>\"Few of the current crop of children's records and songbooks match the sincerity and skill communicated on this album. . . . This a very bright and lively album and a glorious expression of life\" Ã¢ÂÂSing Out!</p><p>\"Drawing heavily from traditional sources (he even makes \"John Henry\" seem new), McCutcheon invests his songs and stories with rustic delight.\" Ã¢ÂÂWashington Post</p><p>Cut the Cake 4:15<br>Howjadoo 2:43<br>Molly and the Whale / Rubber Blubber Whale 6:19<br>John Henry 3:25<br>All God's Critters 2:31<br>Peanut Butter / Peanut Butter 5:37<br>Babysitter 2:30<br>Pap's Billygoat 2:18<br>Here's To Cheshire 5:17<br>Rustic Dance 1:10<br>Father Grumble 2:13<br>Tender Shepherd 2:27</p><br>Year released:&nbsp;<br>&nbsp;<span>1983</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p39_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 40,
          TITLE: "Fine Times at Our House",
          DESCRIPTION:
            'This album features healthy helpings of John\'s stellar hammer dulcimer and fiddle playing, sometimes at the same time, thanks to the wonders of multi-track recording. Joined by the seminal folk ensemble Trapezoid, John reels through a sumptuous collection traditional songs and tunes, from the rollicking "Sally Anne." to the gorgeous "Samanthra." Plenty of unusual tunes he collected in the field and innovative arrangements make this a "must-have" for dulcimer enthusiasts.<br><br>Wild Rose of the Mountain (Si Kahn)/Wild Rose of the Mountain (trad.)<br>HaleÃ¢ÂÂs Rag (trad.)<br>Nancy Ann/Hey, John D, WhereÃ¢ÂÂd You Get Your Britches? (trad)<br>Lonesome John/Fine Times at Our House (trad.)<br>AmeliaÃ¢ÂÂs (Bob McQuillen)<br>Samanthra (trad.)<br>I Am the Bravest Cowboy/CowboyÃ¢ÂÂs Dream (trad.)<br>Times Are Not What They Used to Be (trad.)<br>GrandpaÃ¢ÂÂs Waltz/Clarinet Polka (trad.)<br>Sally Anne (trad.)<br>Back Side of Albany/CooleyÃ¢ÂÂs Reel (trad.)<br>CarolanÃ¢ÂÂs Farewell to Music (OÃ¢ÂÂCarolan)<br><br><br>Year released: 1982<span></span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p40_i1_w170.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 41,
          TITLE: "Barefoot Boy with Boots On",
          DESCRIPTION:
            "<p>Six-time Grammy nominee John McCutcheon has released over twenty albums of old- and new-time American music in the past 25 years. Now, for the first time, this 1980 Front Hall Records release is available on CD. In this wide-ranging collection of fourteen cuts we see the emerging eclecticism that gave birth to one of the most versatile and far-reaching talents in modern folk music. McCutcheon, then in his twenties and already a master of seven different instruments, showcased his love of music of the Carter Family, Roscoe Holcomb, I.D. Stamper, Jimmy Cooper. He also included newly composed music by such traditional Southern writers as Jean Ritchie, Florence Reece, Asa Martin, and Kate Peters Sturgill. Most notably perhaps, this reissue also features the recording debut of John's hammer dulcimer master, Paul Van Arsdale.</p><p>LoggermanÃ¢ÂÂs Breakdown (trad.)/Dulcimer Reel (Paul Van Arsdale) 3:27<br>Little Pink (trad.) 2:28<br>Free Little Bird (trad.) 2:54<br>Laurel Branch (Tommy Hunter)/Ways of the World (trad.)/Sugar in the Gourd (trad.) 4:01<br>Pay Day (trad.) 2:19<br>Barefoot Boy with Boots On (Asa Martin) 3:19<br>Under the Double Eagle (B.F. Wagner)2:41<br>West Virginia Mining Disaster(Jean Ritchie)/Which Side Are You On?(Florence Reece) 5:15<br>Forked Deer (trad.) 2:26<br>Little Moses (trad.) 3:38<br>Unst Wedding March (trad.)/Fanny Poer(Carolan)/Planxty Irwin(Carolan) 4:07<br>Deep Settled Peace (Kate Peters Sturgill) 3:18<br>Peekaboo Waltz(trad.)/Niskayuna Ramble(Paul Van Arsdale) 4:00<br>Ninety Years Old (Frank Taylor &amp; Jack Wright) 2:33</p><br>Year released:&nbsp;<br>&nbsp;<span>1980</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p41_i1_w240.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 42,
          TITLE: "The Wind That Shakes The Barley",
          DESCRIPTION:
            "<p>The Wind That Shakes the Barley, originally released in 1977 on eastern Kentucky's June Appal label, was one of the first all-hammer dulcimer albums in the United States. What it did was expose the most adventurous explorations of the dulcimer up to that time. John McCutcheon, on this his second recording, established himself as one of the most eclectic musicians of the folk music revival. Already a well-known multi-instrumentalist, his expertise and imagination on the hammer dulcimer caused one French periodical to hail this recording as \"a quantum leap in dulcimer playing.\" Since then, McCutcheon has released over thirty other albums of traditional and original music, award winning family recordings, instructional methods, books and, of course, other hammer dulcimer albums. Wind That Shakes the Barley, however, remains a classic recording and an essential part of the modern folk music library.</p><p>Wind that Shakes the Barley 3:30<br>Planxty George Brabazon, Si Bheag Si Mhor 5:47<br>Every Bush and Tree 2:57<br>Dallas Rag 2:53<br>Jesus, Joy of Man's Desiring 2:14<br>Carter Store Medley: Wildwood Flower, Red Wing, Wake Up Susan, Temperance Reel 3:56<br>Sculley's Reel, Morrison's Jig 3:56<br>If I Were a Featherbed 2:44<br>St. Anne's Reel, Cricket on the Hearth, Kitchen Girl, Mississippi Sawyer 4:06<br>Sally in the Garden, Wild Rose of the Mountain 4:10<br>Who Will Sing for Me? 3:18<br>Hangman's Reel, Campbell's Farewell to Red Gap 4:51<br>Greensleeves 1:56<br>Ã¢ÂÂ<br></p>Year released:&nbsp;<br>&nbsp;<span>1977</span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p42_i1_w225.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 43,
          TITLE: "This Land (album download)",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The long-awaited all-Woody Guthrie by John McCutcheon, "This Land: Woody Guthrie\'s America" is slated for a September 15th release here at folkmusic.com. The public release is a month later. It is hailed as one of the most comprehensive and stunning tributes to this American icon. Not only is there an all-star version of "This Land Is Your" (featuring Willie Nelson, among others), but beautiful versions of Guthrie songs, classic and unknown. Joined by a cadre of the finest Americana musicians (Kathy Mattea, Tim O\'Brien, Stuart Duncan, Tommy Emmanuel), John demonstrates not only his superb musicianship, but his understanding of the legacy he is not only celebrating but continuing.</p><p style="color:rgb(0, 0, 0)">Biggest Thing that Man Has Ever Done<br>Mail Myself to You<br>I Ain\'t Got No Home<br>Deportees<br>Harness Up the Day<br>Howjadoo<br>This Morning I Was Born Again<br>Pastures of Plenty<br>1913 Massacre<br>Pretty Boy Floyd<br>Old Cap Moore<br>Ludlow Massacre<br>This Is Our Country Here<br>This Land Is Your Land<br>Hobo\'s Lullaby</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p43_i5_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 44,
          TITLE: "John McCutcheon LIVE! - Concert DVD",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">John McCutcheon, one of the world\'s most gifted folk musicians, songwriters, and storytellers, is featured on the new release JOHN MCCUTCHEON LIVE, a full-length concert DVD recorded on March 30, 2008 at the Ark in Ann Arbor, Michigan. Whether using a guitar, piano, banjo, autoharp, fiddle, hammered dulcimer, or just his own voice, John McCutcheon has an almost otherworldly way of connecting with his audiences through performances that touch on very human levels, often invoking laughter or tears, yet always moving. This DVD captures John at his very best, in concert.</p><p style="color:rgb(0, 0, 0)">Mole in the Ground 12:43<br>Trad., arr. John McCutcheon/Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">L&amp;N DonÃ¢ÂÂt Stop Here Anymore 5:25<br>Jean Ritchie. Geordie Music Publishing (ASCAP)</p><p style="color:rgb(0, 0, 0)">Calling All the Children Home 4:49<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Not Me 5:56<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Minnesota Boogie 1:33<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Puppies 2:18<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Kindergarten Wall 2:41<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Hammer Dulcimer Medly 3:20<br>Rights of Man.<br>Trad., arr. John McCutcheon/Appalsongs (ASCAP)<br>Kitchen Girl<br>Trad., arr. John McCutcheon/Appalsongs (ASCAP)<br>Mississippi Sawyer<br>Trad., arr. John McCutcheon/Appalsongs (ASCAP)<br>Dulcimer Reel<br>Paul Van Arsdale</p><p style="color:rgb(0, 0, 0)">Penny Evans/ CarolanÃ¢ÂÂs Farewell to Music 8:32<br>Steve Goodman. Jurisdad Music (ASCAP)/ Trad., arr.<br>John McCutcheon/Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Mail Myself to You 2:40<br>Woody Guthrie. Ludlow Music (BMI)</p><p style="color:rgb(0, 0, 0)">Great Storm Is Over 4:45<br>Bob Franke. Telephone Pole Music (BMI)</p><p style="color:rgb(0, 0, 0)">Forgive Us 4:11<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Catch 4:17<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">I Am Here 4:38<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Hail to the Chief 5:40<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Joe Hill 12:03<br>Alfred Hayes/Earl Robinson. (Music Sales Corp/Universal Music)</p><p style="color:rgb(0, 0, 0)">Room at the Top of the Stair 6:18<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Not In My Name 4:18<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Leviathan 3:58<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Christmas in the Trenches 8:28<br>John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">HoboÃ¢ÂÂs Lullabye 6:10<br>Reeves Goebel. Sanga Music (BMI)</p><p style="color:rgb(0, 0, 0)">Liza Jane/Breaking Up Christmas 1:36<br>Trad., arr. John McCutcheon. Appalsongs (ASCAP)</p><p style="color:rgb(0, 0, 0)">Ode To Common Things 6:14<br>John McCutcheon. Appalsongs (ASCAP)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p44_i1_w174.jpeg",
          CATEGORIES: "DVDs"
        },
        {
          "PRODUCT ID": 45,
          TITLE: "Happy Adoption Day",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Inspired by a friend\'s tradition, noted children\'s singer/songwriter McCutcheon created this original song for those who might like to mark a special anniversary in their family\'s life?adoption day. His thoughtful lyrics (the score is included, of course) emphasize the joy and wonder of the event?"Out of a world so tattered and torn,/ You came to our house on that wonderful morn/ And all of a sudden this family was born"?and there\'s a rousing chorus just right for a festive party. In a move sure to accommodate many adoptive families, Paschkis (So Sleepy/Wide Awake) pictures the parents as white and the baby as Asian. Her gouache illustrations have a strong hint of traditional Scandinavian folk art, updated by bold color combinations, and they lend themselves particularly well to the multiethnic cast of friends and family with which she peoples each page.</p><p style="color:rgb(0, 0, 0)">NOTE: The hardback edition of "Happy Adoption Day" is now out of print...and Appalseed has the only remaining new copies for sale. Once they\'re gone, they\'re gone.</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p45_i1_w154.jpeg",
          CATEGORIES: "Books"
        },
        {
          "PRODUCT ID": 46,
          TITLE: "Christmas in the Trenches",
          DESCRIPTION:
            '<p>This moving tribute to the power of the human spirit to unite people even in times of battle is based on an actual event from World War I.</p><p>It is cold and clear on Christmas Eve night in 1914. Francis Tolliver and his fellow British soldiers are holed up in muddy trenches along the Western Front. Their enemiesÃ¢ÂÂGerman soldiersÃ¢ÂÂlie in wait just across a field known as "No Man\'s Land."</p><p>Suddenly a strange sound pierces the darkness. Someone is singing a Christmas carol in German. Other German voices join in. When the song ends, Thomas and the other British soldiers sing "God Rest Ye Merry Gentlemen." Soon carols are sung back and forth across No Man\'s Land. Then a figure emerges in the dark, carrying a small Christmas tree with lighted candles. Slowly the British and German soldiers leave their trenches, and the war, behind to stand together in the open field.</p><p>This haunting story is based on an event in World War I known as the Christmas Truce and is adapted by award-winning songwriter John McCutcheon from his song of the same name. Henri SÃÂ¸rensen\'s formal, full-color oil paintings reinforce the emotional power and dignity of the story. The result is a timeless tale that will capture the imagination of readers of all ages.<br>Christmas bonus! A CD featuring readings of the story and recordings of "Silent Night" and "Christmas in the Trenches" is included in every book.</p><p>Intrigued by the story of the Christmas Truce? Interested in learning more about the history and soldiers of World War I? Check out&nbsp;<a data-cke-saved-href="http://www.christmasinthetrenches.info/" href="http://www.christmasinthetrenches.info/">www.christmasinthetrenches.info</a>&nbsp;to learn more about this wonderful book.</p><br><br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p46_i1_w180.gif",
          CATEGORIES: "Books"
        },
        {
          "PRODUCT ID": 47,
          TITLE: "Flowers for Sarajevo",
          DESCRIPTION:
            '<span style="color:rgb(0, 0, 0)"></span>John\'s latest book, illustrated by Kristy Caldwell, is a beautiful telling of the story of Vedran Smailovic, the Cellist of Sarajevo, and his courageous 22-day vigil during the Balkan War. Told from the perspective of a young boy selling flowers in Vase Miniska, we are taken through the days leading up to and through Smailovic\'s wondrous act of defiance and beauty.Ã¢ÂÂ<span style="color:rgb(0, 0, 0)"></span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p47_i1_w240.jpeg",
          CATEGORIES: "Books"
        },
        {
          "PRODUCT ID": 48,
          TITLE: "John McCutcheon's Four Seasons: Autumnsongs",
          DESCRIPTION:
            "<div>Award-winning family music pioneer John McCutcheon continues his Grammy-nominated Four Seasons cycle with Autumnsongs. Once again John serves up a heaping helping of music, fun, and insight. He remembers watching the World Series with his Dad, being the new kid in school, welcoming a noisy new sister into the family, and the quiet reflection of a Thanksgiving Day gathering. He honors farm workersÃ¢ÂÂ leader Cesar Chavez, offers up a new Labor Day anthem and even includes a recipes for sÃ¢ÂÂmores. Once again the music is world class, the songs are unforgettable, and adults are as welcome as children. Prove to yourself that autumn is more than a brief stop between summer and winter. Autumnsongs will have you singing the whole year Ã¢ÂÂround.</div><div><br></div><div>**1998 Parent's Choice Gold Award</div><div>**1999 Grammy Nominee</div><div><br></div><div>ItÃ¢ÂÂs Fall (John McCutcheon &amp; Si Kahn) 2:50</div><div>New Kid in School (John McCutcheon &amp; Si Kahn) 3:29</div><div>Pumpkin Man (John McCutcheon) 2:35</div><div>Halloween (John McCutcheon &amp; Si Kahn) 3:26</div><div>World Series Ã¢ÂÂ57 (John McCutcheon &amp; Si Kahn) 3:26</div><div>Bird Dog (John McCutcheon &amp; Si Kahn) 4:26</div><div>Campfire (John McCutcheon &amp; Si Kahn) 3:30</div><div>Thanksgiving Day (John McCutcheon &amp; Si Kahn) 3:00</div><div>Natural Disaster (John McCutcheon &amp; Si Kahn) 4:10</div><div>Colors (John McCutcheon &amp; Si Kahn) 4:15</div><div>SÃÂ­ Se Puede (John McCutcheon) 2:40</div><div>Labor Day (John McCutcheon &amp; Si Kahn) 3:55</div><div><br></div><div>Year released: &nbsp;1998</div>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p48_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 49,
          TITLE: "John McCutcheon's Four Seasons: Wintersongs",
          DESCRIPTION:
            "<p>Wintersongs is the latest in a stellar collection of award-winning family albums by John McCutcheon. Like his previous five family albums, McCutcheon proves that family music can indeed be child-oriented and truly adult-friendly. Wintersongs celebrates the rituals of winter which mark the memory of every child (and adult), reminding us of experiences at once both personal and universal, from a child's eager anticipation of the first snowfall to memories of the last thaw of winter. John celebrates the things which bring comfort in the cold (such as soup and hot chocolate) and excitement in the short days (skating) and long nights (watching the northern lights), but he also doesn't shy away from the restless discomfort of having the flu. He even sympathizes with the child who wants to hibernate all winter long, sleeping through the bitter cold. Leaving us in anticipation of spring, McCutcheon finds ways for both children and adults to experience the wonder of the year's longest season. As always, the musicianship is superb, the songs are infectious, and the fun is non-stop.</p><p>**1995 ALA (American Library Association) Notable Children's Recording.<br>**1996 Grammy Nominee!!<br>**Top 25 Children's Albums of All Time</p><p>New Boots (John McCutcheon &amp; Si Kahn) 2:47<br>Tommy DonÃ¢ÂÂt Lick That Pipe (John McCutcheon &amp; Si Kahn) 3:02<br>Hot Chocolate (John McCutcheon &amp; Si Kahn) 3:40<br>Soup (John McCutcheon &amp; Si Kahn) 4:10<br>Wintersong (John McCutcheon &amp; Si Kahn) 3:05<br>Aurora (John McCutcheon &amp; Si Kahn) 5:02<br>Hibernation (John McCutcheon &amp; Si Kahn) 3:24<br>The Flu (John McCutcheon &amp; Si Kahn) 2:59<br>Waiting for Snow (John McCutcheon &amp; Si Kahn) 3:05<br>Fly (John McCutcheon &amp; Si Kahn) 2:59<br>Groundhog Day (John McCutcheon &amp; Si Kahn) 2:58<br>Footprints (John McCutcheon &amp; Si Kahn) 3:38</p>Year released:&nbsp;<span>1996</span><br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p49_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 50,
          TITLE: "John McCutcheon's Four Seasons: Summersongs",
          DESCRIPTION:
            "Summersongs is the first of John McCutcheon's Four Seasons series of family albums celebrating each season of the year. McCutcheon, whose previous family albums have received awards from the American Library Association and Parents' Choice Magazine, masterfully evokes children's sentiments of summer, from swimming holes, ice cream men and lawn mowers to backyard camping and meteor showers. Adults will be surprised at how easily their own summer memories return. Come spend the summer with John McCutcheon and this uplifting family recording.<br><br>**Winner of the 1995 NAPPA (National Association of Parenting Publications) Gold Award<br>**ALA (American Library Association) Notable Children's Recording<br>**Grammy nominee for Best Musical Album For Children for 1995<br><br>\"A terrific collection . . . most of the dozen tunes are irresistibly cheerful.\"Ã¢ÂÂBooklist<br><br>\"The first of a planned 'four seasons' series, this John McCutcheon masterpiece just might have you barefoot and mixin' lemonade in the dead of winter. The subject matter of the songs will bring a smile to kids and a memory to adults. . . .\" Ã¢ÂÂSan Diego Parent Magazine<br><br>Swimming Hole (John McCutcheon &amp; Si Kahn) 3:08<br>Mud (John McCutcheon &amp; Si Kahn) 2:36<br>Haircut (John McCutcheon &amp; Si Kahn) 4:30<br>Meteors (John McCutcheon &amp; Si Kahn)/The Perseid (John McCutcheon) 3:56<br>Kid Who Hates Summer (John McCutcheon &amp; Si Kahn) 4:48<br>Dad and Me (John McCutcheon &amp; Si Kahn) 4:09<br>Camping in the Wilderness (John McCutcheon &amp; Si Kahn) 3:36<br>Ice Cream Man (John McCutcheon &amp; Si Kahn) 3:03<br>Power Mower (John McCutcheon &amp; Si Kahn) 3:24<br>Riding My Bike (John McCutcheon &amp; Si Kahn) 2:49<br>Own Backyard (John McCutcheon &amp; Ms. DowdÃ¢ÂÂs 3rd Grade Class) 3:24<br>I Love Summer (John McCutcheon &amp; Si Kahn) 4:08<br><br>Year released: &nbsp;1995<br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p50_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 51,
          TITLE: "Sprout Wings and Fly",
          DESCRIPTION:
            "This album of traditional material includes a handful of tunes not entirely from the standard traditional repertoire. Woody Guthrie's \"Ludlow Massacre\" is included as well as some of John's more traditional-style originals: \"Who'll Rock the Cradle,\" \"Heaven's Wake,\" and \"Road to Bangor.\" In addition to singers Iris Dement, Tim &amp; Molly O'Brien, and Robin &amp; Linda Williams, instrumentation is far-ranging. Not only are there the requisite fiddle, banjos, and hammer dulcimers, John has brought in didgeridoos and African drums...instruments that were traditional long before banjos were invented.<br><br>McCutcheon is a master of traditional music and his return to form is joyous, deep, and tremendously satisfying.<br><br>Who'll Rock the Cradle (McCutcheon) 4:24<br>Jack of Diamonds (traditional)&nbsp;&nbsp; &nbsp;3:45<br>Reuben (traditional)&nbsp;&nbsp; &nbsp;4:54<br>Over the Garden Wall (AP Carter) 3:29<br>Wheels/Tim the Turncoat (traditional) 2:48<br>Ludlow Massacre (Guthrie) 5:01<br>Yellow Rose of Texas (traditional) 2:42<br>Sweet Sunny South (traditional)&nbsp;&nbsp; &nbsp;4:07<br>Heaven's Wake (McCutcheon)&nbsp;&nbsp; &nbsp;4:25<br>Road to Bangor/Morrison's (McCutcheon/traditional) 4:56<br>Oh Death (traditional)&nbsp;&nbsp; &nbsp;3:32<br>Hangman's Reel (traditional) 2:28<br>Time Has Made a Change in Me (traditional) 4:10<br>Cumberland Gap (traditional)&nbsp;&nbsp; &nbsp;1:41<br><br>Year released: &nbsp;1997<br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p51_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 52,
          TITLE: "Bigger Than Yourself",
          DESCRIPTION:
            "Bigger Than Yourself is a collection of fifteen McCutcheon/Kahn originals that deal with pooling ideas and energy, sharing leadership, sticking up for yourself and one another, and sticking together. Kids organize their school to convince a principal of their ideas, figure out how to afford things one can't buy alone, get along with people from different cultures. There's even a song about a babysitter as a replacement worker. It's a ton of fun and, as usual, boasts a world full of musical styles and ideas.<br><br>Bigger Than Yourself was released on Labor Day in 1997, and was immediately adopted by the Pittsburgh Public Schools as a teaching tool. The local Labor Council, in honor of that yearsÃ¢ÂÂ AFL/CIO Convention, made a gift of hundreds of copies of the album to the schools.<br><br>The George Meany Center for Labor Education has developed a great study guide for Bigger Than Yourself. ItÃ¢ÂÂs geared toward classroom use and takes the album one song, one concept at a time. ItÃ¢ÂÂs a great accompaniment to those of you who want to expand upon the ideas presented in this Grammy-nominated collection of songs about fair play, cooperation, collection action, and fun.<br><br>I Got a Dime (John McCutcheon &amp; Si Kahn) 3:58<br>The Principle (John McCutcheon &amp; Si Kahn) 2:43<br>Whatchagonnabe? (John McCutcheon &amp; Si Kahn) 2:46<br>Write It Down (John McCutcheon &amp; Si Kahn) 3:25<br>Someone Else Decide (John McCutcheon &amp; Si Kahn) 3:30<br>Friendship (John McCutcheon &amp; Si Kahn) 4:56<br>Play Fair (John McCutcheon &amp; Si Kahn) 3:25<br>Kids on Strike (John McCutcheon &amp; Si Kahn) 3:29<br>Still the Ones for Me (John McCutcheon &amp; Si Kahn) 2:30<br>Stick Together (John McCutcheon &amp; Si Kahn) 2:55<br>Sing Me (John McCutcheon &amp; Si Kahn) 4:44<br>Friends DonÃ¢ÂÂt Let Friends (John McCutcheon &amp; Si Kahn) 2:54<br>Running for President (John McCutcheon &amp; Si Kahn) 2:11<br>Safe at Home (John McCutcheon &amp; Si Kahn) 2:30<br>Bigger Than Yourself (John McCutcheon &amp; Si Kahn) 4:20<br><br>Year released: &nbsp;1997<br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p52_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 53,
          TITLE: "Doing Our Job",
          DESCRIPTION:
            'This album is the second of John\'s live albums (the first being Live at Wolf Trap), and his first recording with singer-songwriter Tom Chapin. Supported by frequent collaborators Michael Mark and Bobby Read, they plumbed the depths of their musical synchronicity and found a broad swath of common ground. The musical textures vary widely from song to song, the four-part harmonies were an unexpected surprise, and all were blessed with great audiences in good voice. It really turned out to be an ensemble effort rather than a round-robin, one of those rare instances when the total is truly greater than the sum of its parts.<br><br>"John McCutcheon and Tom Chapin do their job to perfection on this joint recording . . . Don\'t walk to the store to buy this recording. Run." Ã¢ÂÂSing Out!<br><br>Well May the World Go (Pete Seeger)&nbsp;&nbsp; &nbsp;2:28<br>Northfield/Pass the Music On (traditional/Si Kahn &amp; Tom Chapin)&nbsp;&nbsp; &nbsp;6:12<br>Pastures of Plenty (Woody Guthrie)&nbsp;&nbsp; &nbsp;3:37<br>Our Mothers Built This City (Si Kahn &amp; Tom Chapin)&nbsp;&nbsp; &nbsp;3:46<br>Doing My Job (John McCutcheon)&nbsp;&nbsp; &nbsp;4:00<br>Every Night (traditional)&nbsp;&nbsp; &nbsp;3:45<br>I Don\'t Care (John McCutcheon)&nbsp;&nbsp; &nbsp;3:35<br>Hard Cider (John McCutcheon &amp; Tom Chapin)&nbsp;&nbsp; &nbsp;4:02<br>Dead Man Walking (John McCutcheon)&nbsp;&nbsp; &nbsp;4:40<br>Make It Right (Tom Chapin)&nbsp;&nbsp; &nbsp;3:53<br>River Gonna Carry Me (John McCutcheon)&nbsp;&nbsp; &nbsp;3:20<br>Heaven Help (John McCutcheon &amp; Tom Chapin)&nbsp;&nbsp; &nbsp;3:57<br>The Older I Get (John McCutcheon &amp; Tom Chapin)&nbsp;&nbsp; &nbsp;3:46<br>Starlight (John McCutcheon)&nbsp;&nbsp; &nbsp;4:58<br>Welcome the Traveler Home (John McCutcheon)&nbsp;&nbsp; &nbsp;3:45<br><br>Year released: &nbsp;1997<br data-cke-eol="1"><br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p53_i1_w179.jpeg",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 54,
          TITLE: "CAMP Reservation - May 19-23, 2019",
          DESCRIPTION:
            "<p>John McCutcheon's 5th Annual Songwriting Camp at Highlander</p><p><strong>Dates for SESSION TWO: June 23rd - 27th, 2019</strong></p><p><br></p><p>Join Grammy-nominated folk musician and songwriter, John McCutcheon, for an intense, intimate songwriting Master Class at the historic Highlander Center in east Tennessee. Join other songwriting lovers for this remarkable event at an even more remarkable place. In between sessions enjoy breathtaking views of the Smoky Mountains, healthy, delicious homemade food, camaraderie, and visits to the Highlander library and archives.</p><p><br></p><p>Camp Fee: $800.00.covers:</p><ul><li>All instruction, workshops, exercises, consultations, materials</li><li>All meals (Sunday supper through Thursday breakfast)</li><li>Lodging (dormitory; see additional private and semi-private options below)</li></ul><p>Lodging private/semi-private options</p><ul><li>$20 extra per night (double occupancy in workshop building)</li><li>$30 extra per night (single occupancy in workshop building)</li><li>$30 extra per night (per person in newly-constructed Lodge)</li></ul><p><br></p><p>A non-refundable $150 deposit is required at registration. Our office staff will contact you to finish the reservation personally so please enter in your preferred contact information.</p><p>Payment options:</p><p>*balance paid in two equal credit card charges automatically paid on April 1st and May 1st</p>",
          IMAGE: "",
          CATEGORIES: "Instruction, Camp Reservations"
        },
        {
          "PRODUCT ID": 55,
          TITLE: "CAMP Reservation - June 23-27, 2019",
          DESCRIPTION:
            "<p>John McCutcheon's 6th Annual Songwriting Camp at Highlander</p><p><strong>Dates for SESSION ONE: May 19th - 21st, 2019</strong></p><p>Join Grammy-nominated folk musician and songwriter, John McCutcheon, for an intense, intimate songwriting Master Class at the historic Highlander Center in east Tennessee. Join other songwriting lovers for this remarkable event at an even more remarkable place. In between sessions enjoy breathtaking views of the Smoky Mountains, healthy, delicious homemade food, camaraderie, and visits to the Highlander library and archives.</p><p><br></p><p>Camp Fee: $800.00.covers:</p><p><br></p><ul><li>All instruction, workshops, exercises, consultations, materials</li><li>All meals (Sunday supper through Thursday breakfast)</li><li>Lodging (dormitory; see additional private and semi-private options below)</li></ul><p><br></p><p>Lodging private/semi-private options</p><p><br></p><ul><li>$20 extra per night (double occupancy in workshop building)</li><li>$30 extra per night (single occupancy in workshop building)</li><li>$30 extra per night (per person in newly-constructed Lodge)</li></ul><p><br></p><p>A non-refundable $150 deposit is required at registration. Our office staff will contact you to finish the reservation personally so please enter in your preferred contact information.</p><p>Payment options:</p><p>*balance paid in two equal credit card charges automatically paid on April 1st and May 1st</p>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p55_i1_w240.jpeg",
          CATEGORIES: "Instruction, Camp Reservations"
        },
        {
          "PRODUCT ID": 56,
          TITLE: "Biggest Thing That Man Has Ever Done",
          DESCRIPTION: "From This Land: Woody Gruthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p56_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 57,
          TITLE: "Mail Myself To You",
          DESCRIPTION:
            "From <strong>This Land: Woody Guthrie's America</strong>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p57_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 58,
          TITLE: "I Ain't Got No Home",
          DESCRIPTION: "From <b>This Land: Woody Guthrie's America</b>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p58_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 60,
          TITLE: "Harness Up The Day",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p60_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 61,
          TITLE: "Howjadoo",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE: "",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 62,
          TITLE: "This Morning I Was Born Again",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p62_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 63,
          TITLE: "Pastures of Plenty",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p63_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 64,
          TITLE: "1913 Massacre",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p64_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 65,
          TITLE: "Pretty Boy Floyd",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p65_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 66,
          TITLE: "Old Cap Moore",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p66_i3_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 67,
          TITLE: "Ludlow Massacre",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p67_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 68,
          TITLE: "This Is Our Country Here",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p68_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 69,
          TITLE: "This Land Is Your Land",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p69_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 70,
          TITLE: "Hobo's Lullaby",
          DESCRIPTION: "From This Land: Woody Guthrie's America",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p70_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 71,
          TITLE: "Long, Long Road to Home",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p71_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 72,
          TITLE: "Sara Tucholsky",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p72_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 73,
          TITLE: "Forget About",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p73_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 74,
          TITLE: "Old People In Love",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p74_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 75,
          TITLE: "Streets Of Sarajevo",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p75_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 76,
          TITLE: "Boys in Green",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p76_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 77,
          TITLE: "El PerdÂon",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p77_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 78,
          TITLE: "Different",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p78_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 79,
          TITLE: "Dreams and Bones",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p79_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 80,
          TITLE: "Daddy Did",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p80_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 81,
          TITLE: "At the Moment",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p81_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 82,
          TITLE: "Prodigal Father",
          DESCRIPTION: "From Untold: Song",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p82_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 83,
          TITLE: "Well May the World Go-Survivor",
          DESCRIPTION: "From Untold: Word",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p83_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 84,
          TITLE: "Sydney-Joe Hill",
          DESCRIPTION: "From Untold: Word",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p84_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 85,
          TITLE: "John Henry",
          DESCRIPTION: "From Untold: Word",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p85_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 86,
          TITLE: "Robbery-Forgive Us",
          DESCRIPTION: "From Untold: Word",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p86_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 87,
          TITLE: "Step by Step-Miracle",
          DESCRIPTION: "From Untold: Word",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p87_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 88,
          TITLE: "Our Flag Was Still There",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p88_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 89,
          TITLE: "La Mujer de Don Miguel",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p89_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 90,
          TITLE: "Claudette Colvin Goes to Work",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p90_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 91,
          TITLE: "Good Ol' Girls",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p91_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 92,
          TITLE: "Dead Man Walking",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p92_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 93,
          TITLE: "Cultivo Una Rosa Blanca",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p93_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 94,
          TITLE: "Harness Up the Day",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p94_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 95,
          TITLE: "Single Girl",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p95_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 96,
          TITLE: "Sail Away",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p96_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 97,
          TITLE: "Para Mi Corazon Basta Tu Pecho",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p97_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 98,
          TITLE: "It's the Economy, Stupid",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p98_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 99,
          TITLE: "Jayber Crow's Silly Song About Jesus",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE: "",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 100,
          TITLE: "Ode to Common Things",
          DESCRIPTION: "From Mightier Than The Sword",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p100_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 101,
          TITLE: "Sermon on the Mound",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p101_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 102,
          TITLE: "Baseball on the Block",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p102_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 103,
          TITLE: "Big",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p103_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 104,
          TITLE: "Doing My Job",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p104_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 105,
          TITLE: "Cross That Line",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p105_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 106,
          TITLE: "One More Mountaintop",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p106_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 107,
          TITLE: "Te Recuerdo",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p107_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 108,
          TITLE: "Catch",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p108_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 109,
          TITLE: "The Star Spangled Banner",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p109_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 110,
          TITLE: "I Am Here",
          DESCRIPTION: "From Hail to the Chief",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p110_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 111,
          TITLE: "Talking Yogi Talk",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p111_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 112,
          TITLE: "Take Me Out to the Ballgame",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p112_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 113,
          TITLE: "World Series '57",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p113_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 114,
          TITLE: "John Rocker",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p114_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 115,
          TITLE: "Modern Kid Blues",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE: "",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 116,
          TITLE: "Hope I Make It",
          DESCRIPTION: "From Sermon on the Mound",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p116_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 117,
          TITLE: "Hope Dies Last",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p117_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 118,
          TITLE: "Not Me",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p118_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 119,
          TITLE: "Simple Man",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p119_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 120,
          TITLE: "Fiddler's Last Dance",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p120_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 121,
          TITLE: "Dick Cheney",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p121_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 122,
          TITLE: "Waiting for a Miracle",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p122_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 123,
          TITLE: "Forgive Us",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p123_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 124,
          TITLE: "SuAnne Big Crow",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p124_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 125,
          TITLE: "Waist Deep in the Big Muddy",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p125_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 126,
          TITLE: "Oprah Seat",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p126_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 127,
          TITLE: "Twenty Todays Ago",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p127_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 128,
          TITLE: "Drive All Night",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p128_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 129,
          TITLE: "Boob on Our TV",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p129_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 130,
          TITLE: "The Other Side",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p130_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 131,
          TITLE: "This Fire",
          DESCRIPTION: "From This Fire: Politics, Love, & Other Small Miracles",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p131_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 132,
          TITLE: "Duct Tape",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p132_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 133,
          TITLE: "The Boys in Green",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p133_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 134,
          TITLE: "Let's Pretend",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p134_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 135,
          TITLE: "We Know War",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p135_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 136,
          TITLE: "Black Sea",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p136_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 137,
          TITLE: "Love & Understanding",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p137_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 138,
          TITLE: "Streets of Sarajevo",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p138_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 139,
          TITLE: "Hey Little Ant",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p139_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 140,
          TITLE: "We Are Not Alone",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p140_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 141,
          TITLE: "The Masters",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p141_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 142,
          TITLE: "Laz'rus",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p142_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 143,
          TITLE: "Stand Up!",
          DESCRIPTION: "From Stand Up!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p143_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 144,
          TITLE: "Ashcroft's Army",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p144_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 145,
          TITLE: "Monkeys",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p145_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 146,
          TITLE: "Talking Tinky-Winky Blues",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p146_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 147,
          TITLE: "Hail to the Chief",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p147_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 148,
          TITLE: "I'm Packin'",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p148_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 149,
          TITLE: "The List",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p149_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 150,
          TITLE: "Take Back the Night",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p150_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 151,
          TITLE: "Let's Keep It Straight",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p151_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 152,
          TITLE: "Picture of Jesus",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p152_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 153,
          TITLE: "Talking Pat & Jerry Blues",
          DESCRIPTION: "From: Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p153_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 154,
          TITLE: "No Turning Back Now",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p154_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 155,
          TITLE: "Just One Voice",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p155_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 156,
          TITLE: "Dearest Martha",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p156_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 157,
          TITLE: "Ask Any Farmer",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p157_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 158,
          TITLE: "Welcome the Traveler Home",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p158_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 159,
          TITLE: "Immigrant",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p159_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 160,
          TITLE: "One Man's Trash",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p160_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 161,
          TITLE: "Follow the Light",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p161_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 162,
          TITLE: "Wish You Goodnight",
          DESCRIPTION: "From Welcome the Traveler Home: the Winfield Songs",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p162_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 163,
          TITLE:
            "Wild Rose of the Mountain (Kahn)/Wild Rose of the Mountain (trad)",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p163_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 164,
          TITLE: "Hale's Rag",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p164_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 165,
          TITLE: "Nancy Ann/Hey, John D, Where'd You Get Your Britches?",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p165_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 166,
          TITLE: "Lonesome John/Fine Times at Our House",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p166_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 167,
          TITLE: "Amelia's Waltz",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p167_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 168,
          TITLE: "Samanthra",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p168_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 169,
          TITLE: "I Am the Bravest Cowboy/Cowboy's Dream",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p169_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 170,
          TITLE: "Times Are Not What They Used to Be",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p170_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 171,
          TITLE: "Grandpa's Waltz/Clarinet Polka",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p171_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 172,
          TITLE: "Sally Anne",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p172_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 173,
          TITLE: "Backside of Albany/Cooley's Reel",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p173_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 174,
          TITLE: "Carolan's Farewell to Music",
          DESCRIPTION: "From Fine Times at Our House",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p174_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 175,
          TITLE: "Greatest Story Never Told",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p175_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 176,
          TITLE: "Ghosts of the Good Old Days",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p176_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 177,
          TITLE: "Dancing in the Street",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p177_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 178,
          TITLE: "Last First Kiss",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p178_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 179,
          TITLE: "Barbershop",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p179_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 180,
          TITLE: "Children of Abraham",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p180_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 181,
          TITLE: "Extend a Hand",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p181_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 182,
          TITLE: "Not in My Name",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p182_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 183,
          TITLE: "When I Grow Up",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p183_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 184,
          TITLE: "Used to Be",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p184_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 185,
          TITLE: "Walk on Water",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p185_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 186,
          TITLE: "One in a Million",
          DESCRIPTION: "From The Greatest Story Never Told",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p186_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 187,
          TITLE: "Casey Jones, the Union Scab",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p187_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 188,
          TITLE: "It's a Long Way Down to the Soup Line",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p188_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 189,
          TITLE: "The Tramp",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p189_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 190,
          TITLE: "Joe Hill's Last Will",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p190_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 191,
          TITLE: "Mr. Block",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p191_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 192,
          TITLE: "What We Want",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p192_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 193,
          TITLE: "The Preacher and the Slave",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p193_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 194,
          TITLE: "Overalls and Snuff/The Connaughtman's Rambles",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p194_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 195,
          TITLE: "The Wooden Shoe/Ta Ra Ra Boom De Ay",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p195_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 196,
          TITLE: "The Rebel Girl",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p196_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 197,
          TITLE: "Stung Right",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p197_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 198,
          TITLE: "Where the Fraser River Flows",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p198_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 199,
          TITLE: "There Is Power in a Union",
          DESCRIPTION: "From Joe Hill's Last Will",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p199_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 200,
          TITLE: "One More Day",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p200_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 201,
          TITLE: "End of the World",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p201_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 202,
          TITLE: "With My Father",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p202_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 203,
          TITLE: "Father Forgive",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p203_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 204,
          TITLE: "You Can't Take It with You",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p204_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 205,
          TITLE: "Glory Halleluiah",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p205_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 206,
          TITLE: "Ode to a Krispy Kreme",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p206_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 207,
          TITLE: "Along Came You",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p207_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 208,
          TITLE: "Tallahassee Waltz",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p208_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 209,
          TITLE: "Las Damas de Blanco",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p209_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 210,
          TITLE: "Friendly Competition",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p210_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 211,
          TITLE: "Iowa",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p211_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 212,
          TITLE: "Your Age",
          DESCRIPTION: "From Passage",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p212_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 213,
          TITLE: "Come Home",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p213_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 214,
          TITLE: "Forgotten",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p214_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 215,
          TITLE: "Fitzgerald",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p215_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 216,
          TITLE: "Of an Age",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p216_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 217,
          TITLE: "Heaven's Kitchen",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p217_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 218,
          TITLE: "Morning",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p218_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 219,
          TITLE: "Dry Land Fish",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p219_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 220,
          TITLE: "Nothing Like You",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p220_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 221,
          TITLE: "The Night That Dan Ryan Got Locked in the Pub",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p221_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 222,
          TITLE: "Orion's Belt",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p222_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 223,
          TITLE: "Tonight",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p223_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 224,
          TITLE: "She Sings",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p224_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 225,
          TITLE: "The Man Walking His Dog",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p225_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 226,
          TITLE: "Adagio in A minor",
          DESCRIPTION: "From 22 Days",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p226_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 227,
          TITLE: "Fine Times at Our House - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">This album features healthy helpings of John\'s stellar hammer dulcimer and fiddle playing, sometimes at the same time, thanks to the wonders of multi-track recording. Joined by the seminal folk ensemble Trapezoid, John reels through a sumptuous collection traditional songs and tunes, from the rollicking "Sally Anne." to the gorgeous "Samanthra." Plenty of unusual tunes he collected in the field and innovative arrangements make this a "must-have" for dulcimer enthusiasts.</p><p style="color:rgb(0, 0, 0)">Wild Rose of the Mountain (Si Kahn)/Wild Rose of the Mountain (trad.)<br>Haleâs Rag (trad.)<br>Nancy Ann/Hey, John D, Whereâd You Get Your Britches? (trad)<br>Lonesome John/Fine Times at Our House (trad.)<br>Ameliaâs (Bob McQuillen)<br>Samanthra (trad.)<br>I Am the Bravest Cowboy/Cowboyâs Dream (trad.)<br>Times Are Not What They Used to Be (trad.)<br>Grandpaâs Waltz/Clarinet Polka (trad.)<br>Sally Anne (trad.)<br>Back Side of Albany/Cooleyâs Reel (trad.)<br>Carolanâs Farewell to Music (OâCarolan)</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p227_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 228,
          TITLE: "The Greatest Story Never Told - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">The energy that John McCutcheon and band bring to this powerful collection of all-new songs is amazing. Marking several milestones (his 50th birthday, 30 years in music and his first CD on a new label), the songs deliver powerfully concise observations on where weâve been, where we are and where we are going. Blending rock colorations with acoustic sensibilities, this project has a refreshing and cohesive integrity. TIM OâBRIEN and Australian KERRIANNE COX make guest appearances and Johnâs gift for weaving astute commentary with crisp song writing and instrumental expertise is manifest through out the CD.</p><p style="color:rgb(0, 0, 0)">Greatest Story Never Told 4:14<br>Ghosts of the Good Old Days 3:05<br>Dancing in the Street 5:01<br>Last First Kiss 3:45<br>Barbershop 3:03<br>Children of Abraham 3:44<br>Extend a Hand 6:03<br>Follow the Light 4:19<br>Not in My Name 4:34<br>When I Grow Up 3:15<br>Used to Be 4:21<br>Walk on Water 4:16<br>One in a Million 4:14</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p228_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 229,
          TITLE: "Welcome the Traveler Home - album download",
          DESCRIPTION:
            "In the spring of 1979, Art Coates called wondering if I'd attend a festival he was booking in Kansas. He'd heard my recordings and figured his neighbors might enjoy my music. I suggested he hire me as part of the band I was working with at the time--Wry Straw. He said yes, and so did I.<br><span></span>That visit to the small town of Winfield would be the first of many. I returned often in twenty-five years, forging lasting friendships and discovering musical collaborators. I learned about wheat farming, cattle ranching, local legends, hometown orchestras, hobo eggs and calf fries.<br><span></span>I've seen romances bloom, and fade. Seen children come, and grow. And I've buried friends. Through mud, drought, dust storms and September 11th, I've joined this far-flung family that gathers for one weekend each year. It is unlike any other festival I attend and Iâm humbled to be welcomed by these good people.<br><span></span>I'm a Midwestern kid at heart. I came from a small town, with small town sensibilities. And as I wedded the remembrances of my past with the things I learned from these sturdy Kansans--the songs nearly wrote themselves. Songs which fell naturally between the fencerows of Walnut Valley. More songs followed. But I always knew where they came from ... and belonged. Most years I composed a new song with these people in mind: waiting to be sung just for them. Oh, other audiences may have heard them first. But no one ever listened to them, understood them, in the way Winfield did.<br><span></span>So, this is my gift to the Winfield family: a collection of thirteen songs, birthed over the years, from 1979 through 2004. The newest, \"Just One Voice,\" speaks best of what I've learned from this diverse, generous audience: that from the simplest, humblest beginnings, amazing things may spring.<br><span></span>No Turning Back Now 2:53<br>Just One Voice 3:36<br>One More Mountaintop 4:22<br>Dearest Martha 3:57<br>Ask Any Farmer 4:52<br>Welcome the Traveler Home 3:45<br>Doing Our Job 4:00<br>Immigrant 5:25<br>Monkeys 2:56<br>One Man's Trash 4:24<br>Follow the Light 4:19<br>Ashcroft's Army 2:57<br>Wish You Goodnight 4:02<br><span></span><br><br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p229_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 230,
          TITLE: "Hail to the Chief! - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Folks, John has happily "retired" the many songs he wrote during the 8 years of the previous Administration. He\'s sent them all down to Crawford, TX where they\'ll relax clearing brush for the remainder of their days. Until recently, we believed this was completely out of print, but a small number turned up in a recent office move, so it\'s back for now! And this time, when they\'re gone, they\'re gone. Download is also available from the Audio Download page.</p><p style="color:rgb(0, 0, 0)">Be one of the last people to actually have recordings of "Ashcroft\'s Army," "Let\'s Pretend," "Talking Pat and Jerry Blues," "The List," and the classic, "Hail to the Chief."</p><p style="color:rgb(0, 0, 0)">And never fear! John realizes that some of the songs on each of these albums have a longer shelf-life than 43. So a new album, gathering the more universal of the songs into a new recording that will include many of the newer topical songs dealing with all things post-W. Stay tuned to the News section of the www site for updates.</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p230_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 231,
          TITLE: "Stand Up! - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Following on the heels of the incredibly popular 2003 release, "Hail to the Chief," John McCutcheon delivers another batch of hard-hitting, laugh-out-loud, timely songs in "Stand Up!" From aircraft carrier landings to duct tape, from Iraq to Alaska, from sending up Pat Robertson for "praying out a contract on the Supreme Court" to honoring Vedran Smalovik\'s cello playing in the streets of Sarajevo, McCutcheon proves what an incisive eye, a wicked wit and a fierce intelligence can do with topcial songwriting. With "Hail to the Chief" he was called "...one of the very few and very best of our political songwriters." With "Stand Up!" he proves what an inspiring world we live in and what an interesting year we\'ve had.</p><p style="color:rgb(0, 0, 0)">Duct Tape 3:35<br>Boys in Green 3:13<br>Let\'s Pretend 3:28<br>We Know War 4:24<br>Black Sea 3:00<br>At the Moment 4:23<br>Different 3:02<br>Love &amp; Understanding 4:01<br>Streets of Sarajevo 4:39<br>Hey Little Ant 3:11<br>We Are Not Alone 3:11<br>The Masters 1:54<br>Laz\'rus 3:54<br>Stand Up 4:37</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p231_i2_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 232,
          TITLE:
            "This Fire: Love, Politics and Other Small Miracles - album download",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p232_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 233,
          TITLE: "Sermon on the Mound - album download",
          DESCRIPTION:
            "<p>\"Some people say there are better games than baseball. They are wrong.\"<br>--Tom Boswell, The Washington Post</p><p>\"The first thing in my life I ever did right,\" muses John McCutcheon, \"was baseball.\" Since that day in 1959 when the lanky seven-year-old showed up a year too early for Little League tryouts (they took him anyway) McCutcheon has done quite a few other things right. With over thirty-five years of international concert touring, six Grammy nominations, countless awards, over thirty recordings and numerous books under his belt, he's been a busy man. With the release of Sermon on the Mound he's finally brought together two lifelong loves: music and baseball.</p><p>Whether honoring the games heroes (Roberto Clemente, Cal Ripkin Jr., Jackie Robinson, PeeWee Reese), tackling the game's foul balls (steroids, John Rocker), celebrating street ball and Little League, or distilling it all down to its essence (the universal and heart-rending 'Catch'), once again, McCutcheon's pen and eye are wise, bittersweet, and wickedly funny. A home run of an album!</p><p>Sermon on the Mound (4:17)<br>Baseball on the Block (5:43)<br>Big (3:51)<br>Doing My Job (4:03)<br>Cross That Line (4:57)<br>One More Mountaintop (4:22)<br>Te Recuerdo (4:27)<br>Catch (3:55)<br>The Star Spangled Banner (1:30)<br>I Am Here (4:41)<br>Talking Yogi Talk (2:37)<br>Take Me Out to the Ballgame (0:41)<br>World Series â57 (3:35)<br>John Rocker (2:58)<br>Modern Kid Blues (4:30)<br>Hope I Make It (4:19)</p><br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p233_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 234,
          TITLE: "Mightier Than The Sword - album download",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p234_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 235,
          TITLE: "Untold: Word - album download",
          DESCRIPTION:
            'This special double-CD release is the first recording that shows the breadth of John McCutcheon\'s gifts. "Untold" features one disk that was recorded live at the 2008 National Storytelling Festival. It is the first in-depth exploration of John\'s prodigious gift as a storyteller. The second disk features three refugees from the soon-to-be out-of-print "Stand Up" and "Hail to the Chief" and a wealth of new songs audiences have heard in concert the past year. Of special note is a re-recording of "Streets of Sarajevo" with accompaniment by Vedran Smailovic, the Cellist of Sarajevo, a beautiful duet with Suzy Bogguss on John\'s "Old People in Love, " and the much-requested "Sara Tucholsky."<br><br><span></span>STORIES:<br>Survivor-Well May the World Go/<br>Sydney-Joe Hill/<br>John Henry/<br>Robbery-Forgive Us/<br>Miracle-Step by Step<br><span></span>',
          IMAGE: "",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 236,
          TITLE: "Untold: Song - album download",
          DESCRIPTION:
            'This special double-CD release is the first recording that shows the breadth of John McCutcheon\'s gifts. "Untold" features one disk that was recorded live at the 2008 National Storytelling Festival. It is the first in-depth exploration of John\'s prodigious gift as a storyteller. The second disk features three refugees from the soon-to-be out-of-print "Stand Up" and "Hail to the Chief" and a wealth of new songs audiences have heard in concert the past year. Of special note is a re-recording of "Streets of Sarajevo" with accompaniment by Vedran Smailovic, the Cellist of Sarajevo, a beautiful duet with Suzy Bogguss on John\'s "Old People in Love, " and the much-requested "Sara Tucholsky."<br><span></span>SONGS:<br>Long, Long Road to Home/<br>Sara Tucholsky/<br>Forget About/<br>Old People in Love (with Suzy Bogguss)/<br>Streets of Sarajevo (with Vedran Smailovic)/<br>Boys in Green/<br>El PerdÃ³n/<br>Different/<br>Dreams &amp; Bones/<br>Daddy Did/<br>At the Moment/<br>Prodigal Father<br><br><span></span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p236_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 237,
          TITLE: "Passage - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">With his astonishing 34th recording, Passage, folk music stalwart John McCutcheon comes full-circle. He joyously returns to many of the Appalachian sounds and themes that marked the music he played and loved music when he first came into international prominence. With a core band featuring mandolin ace Tim OâBrien, fiddler Stuart Duncan, and bassist Bryn Davies, McCutcheon adds his own vocal, fiddle, banjo, octave mandolin, hammer dulcimer, guitar, piano, jaw harp, and harmonium skills. Singers Kathy Mattea, Suzy Bogguss, and Mollie O\'Brien round out the singing duties. But at the center of this all-star cast of musicians are the songs themselves. Rich, diverse, rooted, moving.</p><p style="color:rgb(0, 0, 0)">Pointedly contemporary, the opening cut, One More Day, is written from the perspective of one of the surviving miners in the Massey explosion in Montcoal, WV just this past spring. End of the World is the story of a Vietnamese-American shrimp boat captain in the immediate aftermath of the Gulf oil spill. Las Damas de Blanco tells of Cubaâs La-dies in White who march in protest of their sons, husbands, and fathers held as political prisoners. Your Age is a recollection of conversations with many older coal miners. Glory Halleluiah is an old-time string band rave-up with Tim and John adding increas-ingly wacky instrumentation that would have made Mike Seeger proud. Tallahassee Waltz is a gorgeous duet with Suzy Bogguss that will send many a couple out on the dance floor. And Ode to a Krispy Kreme is one of the most hilarious and spot-on spoken word narratives youâre likely to hear.</p><p style="color:rgb(0, 0, 0)">But the Passage in the album is also personal. Father Forgive is the story of Johnâs great-grandfather, Michael Abts, immigrating to America. Along Came You is a gift to his first grandchild. Iowa and With My Father both talk of his fatherâs struggle with Alzheimerâs. You Canât Take It with You was written after one of Johnâs best friends died suddenly. And the albumâs closer, Come Home, is a tribute to one of Johnâs men-tors, the WV ballad singer and union activist, Nimrod Workman.</p><p style="color:rgb(0, 0, 0)">John McCutcheon is one of the most prolific, dependable, and entertaining musicians working today. âThe perfect example of a modern folksinger,â is Sing Out! Magazineâs description. âA national treasure!â heralded the Oakland Tribute. And for nearly forty years, continuing to create music that marks our lives and our time here.</p><p style="color:rgb(0, 0, 0)">One More Day (McCutcheon) 4:02<br>End of the World (McCutcheon) 3:51<br>With My Father (McCutcheon) 2:53<br>Tallahassee Waltz (McCutcheon) 3:53<br>Father Forgive (McCutcheon) 5:14<br>You Canât Take It With You (McCutcheon) 3:27<br>Glory Halleluiah (McCutcheon) 3:41<br>Ode to a Krispy Kreme (McCutcheon) 3:01<br>Along Came (McCutcheon) You 3:28<br>Las Damas de Blanco (McCutcheon) 4:05<br>Friendly Competition (McCutcheon) 3:12<br>Iowa (McCutcheon) 3:20<br>Your Age (McCutcheon) 3:16<br>Come Home: (McCutcheon &amp; Si Kahn) 4:28</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p237_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 238,
          TITLE: "22 Days - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">22 Days began as an homage to my friend, Vedran Smailovic, the âCellist of Sarajevo,â who, in honor of 22 people killed by a bomb in a Bosnian breadline, played for 22 days in a row at the bombing site. 20 years to the day of the beginning of Smailovicâs action I sat down for the same number of days, at the same hour every day, to write. There was no goal, no album in sight. I simply wanted to write and see what happened. Over 30 new songs is what happened. With a couple of exceptions, it is songs from that writing intensive that comprise the songs of 22 Days.</p><p style="color:rgb(0, 0, 0)">Some songs have been heard, as theyâve been finished, in concerts throughout the past year. Those of you in the Song of the Month Club have heard one each monthâ¦and, in fact, helped hone them with me. And they are a diverse lot: several love songs, a song about a small South Georgia town, a topical song or two, an instrumental, a hillbilly sea shanty, and a even a kind of follow-up to the Ode to a Krispy Kreme from the Passage album a few years ago.</p><p style="color:rgb(0, 0, 0)">Some of the songs I recorded in my studio here in Georgia, some overdubs with pals in Nashville, and all the vocals and mixing done back at Bias Studios up in Virginia, where I recorded for over 25 years.</p><p style="color:rgb(0, 0, 0)">Forgotten<br>Fitzgerald<br>Of an Age<br>Heavenâs Kitchen<br>Morning<br>Dry Land Fish<br>Nothing Like You<br>Orionâs Belt<br>The Night That Dan Ryan Got Locked in the Pub<br>Tonight<br>She Sings<br>The Man Walking His Dog<br>Adagio in Am</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p238_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 239,
          TITLE: "Joe Hill's Last Will - album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Joe Hill was a songwriter for the Industrial Workers of the World, the Wobblies, back in the early 20th century. He was the ultimate utilitarian songwriter, composing pieces to be used at meetings and picket lines and rallies. He wrote songs to be sung and to be used. To be useful. His songs "The Preacher &amp; the Slave" and "Casey Jones, the Union Scab" are what some people know of his work. But veteran folk musician and longtime labor activist, John McCutcheon, has released an album bringing Joe Hill\'s music to a whole new audience. With fresh arrangements, stunning musicianship, and released on a palette that makes these songs feel as though they were written today rather than a century ago, there is a life and vitality that is both rare and refreshing.</p><p style="color:rgb(0, 0, 0)">Joe Hill was executed by a Utah firing squad at dawn, November 19, 1915. This album is being released in honor of the centenary of Hill\'s death.</p><p style="color:rgb(0, 0, 0)">Casey Jones<br>Itâs a Long Way Down to the Soup Line<br>The Tramp<br>Joe Hillâs Last Will<br>Mr. Block<br>What We Want<br>The Preacher &amp; the Slave<br>Overalls &amp; Snuff/The Connaughtmanâs Rambles<br>The Wooden Shoe/Ta Ra Ra Boom De Ay<br>The Rebel Girl<br>Stung Right<br>Where the Fraser River Flows<br>There Is Power in a Union</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p239_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 240,
          TITLE: "Untold: Word and Song - double album download",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">This special double-CD release is the first recording that shows the breadth of John McCutcheon\'s gifts. "Untold" features one disk that was recorded live at the 2008 National Storytelling Festival. It is the first in-depth exploration of John\'s prodigious gift as a storyteller. The second disk features three refugees from the soon-to-be out-of-print "Stand Up" and "Hail to the Chief" and a wealth of new songs audiences have heard in concert the past year. Of special note is a re-recording of "Streets of Sarajevo" with accompaniment by Vedran Smailovic, the Cellist of Sarajevo, a beautiful duet with Suzy Bogguss on John\'s "Old People in Love, " and the much-requested "Sara Tucholsky."</p><p style="color:rgb(0, 0, 0)">SONGS:<br>Long, Long Road to Home/<br>Sara Tucholsky/<br>Forget About/<br>Old People in Love (with Suzy Bogguss)/<br>Streets of Sarajevo (with Vedran Smailovic)/<br>Boys in Green/<br>El PerdÃ³n/<br>Different/<br>Dreams &amp; Bones/<br>Daddy Did/<br>At the Moment/<br>Prodigal Father</p><p style="color:rgb(0, 0, 0)">STORIES:<br>Survivor-Well May the World Go/<br>Sydney-Joe Hill/<br>John Henry/<br>Robbery-Forgive Us/<br>Miracle-Step by Step</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p240_i1_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 241,
          TITLE: "John Rocker",
          DESCRIPTION: "From Hail To The Chief",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p241_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 242,
          TITLE: "It's the Economy, Stupid",
          DESCRIPTION: "From Hail to the Chief!",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p242_i3_w512.png",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 244,
          TITLE: "The Hammer Dulcimer (6 CDs and Booklet)",
          DESCRIPTION:
            "<p style=\"margin-bottom: 1em; padding: 0px; font-size: 13px; line-height: 1.6em; color: rgb(0, 0, 0); font-family: &quot;Myriad Pro&quot;, Myriad, &quot;Trebuchet MS&quot;, Arial, Helvetica, sans-serif; background-color: rgb(255, 255, 255);\">A complete course in the hammer dulcimer, taught by one of its leading players. John McCutcheon starts at the beginning, introducing you to the instrument and leading you through a myriad of tunes and techniques to make you an accomplished and versatile instrumentalist. You'll learn a repertoire of more than 20 tunes and variations, in several keys, rhythms and styles.</p><p style=\"margin-top: 1em; margin-bottom: 1em; padding: 0px; font-size: 13px; line-height: 1.6em; color: rgb(0, 0, 0); font-family: &quot;Myriad Pro&quot;, Myriad, &quot;Trebuchet MS&quot;, Arial, Helvetica, sans-serif; background-color: rgb(255, 255, 255);\">Songs: Golden Slippers; Mississippi Sawyer; Morrison's Jig; Hog Eye; Leather Britches; Grandpa's Waltz; Jesu, Joy Of Man's Desiring; Cuckoo's Nest; Ragtime; Dulcimer Reel; Hale's Rag; I Don't Love Nobody; Staten Island; Rustic Dance; Clarinet Polka; Baker's March; Under The Double Eagle; Planxty Irwin; Carolan's Welcome; Shebeg Shemore; If I Were A Featherbed; Ragtime Annie.</p>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p244_i1_w150.jpeg",
          CATEGORIES: "CDs, Instruction"
        },
        {
          "PRODUCT ID": 245,
          TITLE: "Hammer Dulcimer Repertoire CD",
          DESCRIPTION:
            '<p style="margin-bottom: 1em; padding: 0px; font-size: 13px; line-height: 1.6em; color: rgb(0, 0, 0); font-family: &quot;Myriad Pro&quot;, Myriad, &quot;Trebuchet MS&quot;, Arial, Helvetica, sans-serif; background-color: rgb(255, 255, 255);">John McCutcheon has chosen nine pieces from his performing repertoire to present with slowed-down versions, tips on technique and a tab booklet.</p><p style="margin-top: 1em; margin-bottom: 1em; padding: 0px; font-size: 13px; line-height: 1.6em; color: rgb(0, 0, 0); font-family: &quot;Myriad Pro&quot;, Myriad, &quot;Trebuchet MS&quot;, Arial, Helvetica, sans-serif; background-color: rgb(255, 255, 255);">Songs: Willie\'s Waltz, Jaybird, Star Of The County Down, Blackberry Blossom, Back Side Of Albany, Big John MacNeil, Unst Wedding March, Flying Cloud Cotillion.</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p245_i1_w150.jpeg",
          CATEGORIES: "CDs, Instruction"
        },
        {
          "PRODUCT ID": 246,
          TITLE: "Ghost Light Associate Producer Package",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Support the production of this new recording by signing on as an Associate Producer. You\'ll receive:</p><p style="color:rgb(0, 0, 0)">*a credit as Associate Producer on the album artwork<br>*a personalized, signed copy of the album, the very first to be shipped out<br>*a free download of the album<br>*4 tickets to a concert of your choice<br>*a personal note from John thanking you for your support</p><p style="color:rgb(0, 0, 0)">THIS IS AN ADVANCE ORDER. RELEASE DATE PROJECTED TO BE NOVEMBER 15TH.<br>John\'s stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, "The Machine," written after the violence in Charlottesville, VA this summer.</p><p style="color:rgb(0, 0, 0)">Ghost Light<br>Unaware<br>Me &amp; Jesus<br>Waiting for the Rain<br>Dark Side of This Town<br>The Story of Abe<br>A Perfect Day<br>Burley Coulter at the Bank<br>When My Fight for Life Is Over<br>She Just Dances<br>Big Day<br>This Road<br>The Machine</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p246_i1_w240.jpeg",
          CATEGORIES: "CDs, Downloads"
        },
        {
          "PRODUCT ID": 247,
          TITLE: "Ghost Light Special Thanks Package",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Support the production of this new recording at this level. You\'ll receive:</p><p style="color:rgb(0, 0, 0)">*a Special Thanks on the album artwork<br>*a personalized, signed copy of the album, the very first to be shipped out<br>*a free download of the album<br>*2 tickets to a concert of your choice<br>*a personal note from John thanking you for your support</p><span></span>THIS IS AN ADVANCE ORDER. RELEASE DATE PROJECTED TO BE NOVEMBER 15TH.<br>John\'s stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, "The Machine," written after the violence in Charlottesville, VA this summer.<br><span></span>Ghost Light<br>Unaware<br>Me &amp; Jesus<br>Waiting for the Rain<br>Dark Side of This Town<br>The Story of Abe<br>A Perfect Day<br>Burley Coulter at the Bank<br>When My Fight for Life Is Over<br>She Just Dances<br>Big Day<br>This Road<br>The Machine<br><span></span>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p247_i1_w240.jpeg",
          CATEGORIES: "CDs, Downloads"
        },
        {
          "PRODUCT ID": 249,
          TITLE: "Ghost Light Concert Comp Package",
          DESCRIPTION:
            '<p style="color:rgb(0, 0, 0)">Support the production of this new recording at this level and you\'ll receive:</p><p style="color:rgb(0, 0, 0)">*a personalized, signed copy of the album, the very first to be shipped out<br>*a free download of the album<br>*2 tickets to a concert of your choice</p><p style="color:rgb(0, 0, 0)">THIS IS AN ADVANCE ORDER. RELEASE DATE PROJECTED TO BE NOVEMBER 15TH.<br>John\'s stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, "The Machine," written after the violence in Charlottesville, VA this summer.</p><p style="color:rgb(0, 0, 0)">Ghost Light<br>Unaware<br>Me &amp; Jesus<br>Waiting for the Rain<br>Dark Side of This Town<br>The Story of Abe<br>A Perfect Day<br>Burley Coulter at the Bank<br>When My Fight for Life Is Over<br>She Just Dances<br>Big Day<br>This Road<br>The Machine</p>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p249_i2_w563.png",
          CATEGORIES: "CDs, Downloads"
        },
        {
          "PRODUCT ID": 250,
          TITLE: "Ghost Light",
          DESCRIPTION:
            'John\'s stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, "The Machine," written after the violence in Charlottesville, VA this summer. ​ <br><br>Ghost Light <br>Unaware <br>Me &amp; Jesus <br>Waiting for the Rain <br>Dark Side of This Town <br>The Story of Abe <br>A Perfect Day <br>Burley Coulter at the Bank <br>When My Fight for Life Is Over <br>She Just Dances <br>Big Day <br>This Road <br>The Machine<br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p250_i2_w563.png",
          CATEGORIES: "CDs"
        },
        {
          "PRODUCT ID": 252,
          TITLE: "Ghost Light 50 package",
          DESCRIPTION:
            "Support the production of this new recording by signing on as an Associate Producer. You'll receive:<br><span></span>*a free download of the album<br>*a personalized, signed copy of the album, the very first to be shipped out<br><span></span>THIS IS AN ADVANCE ORDER. RELEASE DATE PROJECTED TO BE NOVEMBER 15TH.<br>John's stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, \"The Machine,\" written after the violence in Charlottesville, VA this summer.<br><span></span>Ghost Light<br>Unaware<br>Me &amp; Jesus<br>Waiting for the Rain<br>Dark Side of This Town<br>The Story of Abe<br>A Perfect Day<br>Burley Coulter at the Bank<br>When My Fight for Life Is Over<br>She Just Dances<br>Big Day<br>This Road<br>The Machine<br><span></span>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p252_i2_w563.png",
          CATEGORIES: "CDs, Downloads"
        },
        {
          "PRODUCT ID": 255,
          TITLE: "The Machine",
          DESCRIPTION:
            "Here's a new song, a demo prepped for the \"Ghost Light\" album, written after the deadly Charlottesville, VA events. Post it, share it, sing it, broadcast it, use it. It's free. Be the Machine!<br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p255_i1_w108.jpeg",
          CATEGORIES: "Free Download"
        },
        {
          "PRODUCT ID": 256,
          TITLE: "Ghost Light - album download",
          DESCRIPTION:
            'John\'s stunning new album of brand-new songs covers all the bases: love, aging, changing times, faith, grandbabies dancing, and, story of heart-stopping redemption. Also included is a stunning Woody Guthrie-McCutcheon collaboration that has been wowing concert audiences this year. Also included is a bonus track, "The Machine," written after the violence in Charlottesville, VA this summer. ​&nbsp;<br><br>Ghost Light&nbsp;<br>Unaware&nbsp;<br>Me &amp; Jesus&nbsp;<br>Waiting for the Rain&nbsp;<br>Dark Side of This Town&nbsp;<br>The Story of Abe&nbsp;<br>A Perfect Day&nbsp;<br>Burley Coulter at the Bank&nbsp;<br>When My Fight for Life Is Over&nbsp;<br>She Just Dances&nbsp;<br>Big Day&nbsp;<br>This Road&nbsp;<br>The Machine<br>',
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p256_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 257,
          TITLE: "A Perfect Day",
          DESCRIPTION: "<br>",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p257_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 258,
          TITLE: "This Road",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p258_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 259,
          TITLE: "Big Day",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p259_i2_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 261,
          TITLE: "The Machine",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p261_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 262,
          TITLE: "Ghost Light",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p262_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 263,
          TITLE: "Waiting for the Rain",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p263_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 264,
          TITLE: "Burley Coulter at the Bank",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p264_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 265,
          TITLE: "Unaware",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p265_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 266,
          TITLE: "Dark Side of This Town",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p266_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 267,
          TITLE: "Me and Jesus",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p267_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 268,
          TITLE: "Story of Abe",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p268_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        },
        {
          "PRODUCT ID": 269,
          TITLE: "When My Fight For Life Is Over",
          DESCRIPTION: "",
          IMAGE:
            "http://www.folkmusic.com/uploads/1/0/1/6/101699866/s860534000896315264_p269_i1_w512.jpeg",
          CATEGORIES: "Downloads"
        }
      ]
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  font-size: inherit;
}
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
