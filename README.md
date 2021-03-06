'use strict';
var Alexa = require("alexa-sdk");

var date =[
    {"year":"1912","event":"Founder, Tokuji Hayakawa, invents the Tokubijo snap buckle and acquires utility model design patent. Establishes metalworking shop in Matsui-cho, Honjo-ku, Tokyo (now Shin-ohashi, Koto-ku, Tokyo) on September 15. "},
    {"year":"1914","event":"Moves to Hayashi-cho, Honjo-ku, Tokyo (now Tachikawa, Sumida-ku, Tokyo). Installs one-horsepower electric motor. "},
    {"year":"1915","event":"Invents Hayakawa Mechanical Pencil and begins export to the US and Europe. Establishes Hayakawa Brothers Shokai. "},
    {"year":"1920","event":"Establishes branch factory in Oshiage, Tokyo (now Yahiro, Sumida-ku, Tokyo). "},
    {"year":"1923","event":"All factories destroyed during Great Kanto Earthquake. Dissolves Hayakawa Brothers Shokai and relocates to Osaka. "},
    {"year":"1924","event":"Establishes Hayakawa Metal Works in Tanabe-cho, Higashinari-gun, Osaka Prefecture (now the location of the Head Office). "},
    {"year":"1925","event":"Succeeds in assembling first Japan-made crystal radio set; begins mass production and sales. Establishes sales office in Utsubo, Osaka. "},
    {"year":"1926","event":"Begins export of radio sets and components to China, Southeast Asia, India, and South America. Establishes Tokyo office in Hayashi-cho (Honjo-ku, Tokyo), a former site of the company’s factory. Adopts assembly-line production for radios. "},
    {"year":"1927","event":"Holds Sharp radio trade fairs in Kyushu, Japan and Shanghai, China. "},
    {"year":"1929","event":"Releases AC vacuum-tube radios. "},
    {"year":"1930","event":"Hayakawa tours Hong Kong. Begins attaching repair notices to radios. Retailers would notify the company of repairs they did by sending back these notices to the company.. "},
    {"year":"1931","event":"Establishes sales agency in Hong Kong. "},
    {"year":"1934","event":"Establishes Shanghai office. Constructs Hirano Plant in Osaka. "},
    {"year":"1935","event":"Hayakawa Metal Works Institute Co. incorporated with capital of 300,000 yen (May 1). Youths’ School Ordinance issued in Japan. "},
    {"year":"1936","event":"Installs intermittent belt conveyor system. Makes Yokohama Motor Parts Manufacturing a subsidiary. Changes company name to Hayakawa Metal Works Co.. Establishes branch offices in Taipei and Seoul. "},
    {"year":"1937","event":"Establishes Hayakawa Commercial School for Youth. "},
    {"year":"1942","event":"Changes company name to Hayakawa Electric Industry Co., Ltd.. "},
    {"year":"1943","event":"Head office building completed. "},
    {"year":"1944","event":"Establishes Hayakawa Electric branch factory. Establishes Izumi Plant in Izumi-cho (now Izumi City), Osaka (sold in 1948). "},
    {"year":"1945","event":"Establishes Kyoto Plant in Shimogyo-ku (now Minami-ku), Kyoto (sold in 1947). "},
    {"year":"1946","event":"Forms labor union. Designated special accounting company. "},
    {"year":"1948","event":"Establishes Sharp Shoji. "},
    {"year":"1949","event":"Released from special accounting company designation. Public stock offering, company listed on Osaka Securities Exchange. "},
    {"year":"1950","event":"Plant to employ the visually impaired incorporated as Tokusen Metal Limited Partnership. Establishes business principles called the Five Accumulations of Competency. "},
    {"year":"1951","event":"Successfully develops prototype TV set. "},{"year":"1952","event":"Begins publication of Sharp News, an information magazine for retailers. Special bus begins touring the country to advertise Sharp radios and TVs. Signs cooperative agreement with RCA of the US for TV technology. Forms Sharp Friends Club to strengthen ties between dealers, retailers, and the company. "},
    {"year":"1953","event":"Begins full-scale mass production of first Japan-made TV sets (TV3-14T). "},
    {"year":"1954","event":"Constructs TV plant at the head office (now Tanabe Plant, Osaka) and installs endless conveyor system. Opens Ikutoku-en nursery school. "},
    {"year":"1955","event":"Formulates in-house standards (HS: Hayakawa Standards). "},
    {"year":"1956","event":"Spins off sales division to establish Sharp Electric Co.. Constructs new building for Osaka Head Office. Constructs new building for Tokyo Branch in Taito-ku, Tokyo. "},
    {"year":"1957","event":"Establishes Tokyo Sharp Geppan to sell Sharp products on monthly installment system; Sharp Geppan companies subsequently established nationwide. Constructs Hirano Plant No. 2 in Higashi-sumiyoshi-ku (now Hirano-ku), Osaka. Releases transistor radios. Establishes laboratory. "},
    {"year":"1958","event":"Begins publication of Mado, an in-house magazine. Sharp Electric merges with Hayakawa Dengyo, a company that sold fluorescent lighting. Sharp Shoji and QRK Shokai (exclusive Sharp dealer) combined to form Osaka Sharp Sales (regional sales companies subsequently established). Institutes Sharp Friend Shop system; Sharp Friend Shop Associations formed nationwide. "},
    {"year":"1959","event":"Begins R&D on solar cells. Constructs Yao Plant as company moves to become a comprehensive consumer electronics manufacturer. Expands sales network in Southeast Asia by signing dealer agreements with Sampo Electronics and Roxy Electric. "},
    {"year":"1960","event":"Constructs Yamato-koriyama Plant No. 1 (now Nara Plant). Establishes corporate health insurance association. Introduces IBM computer at the head office. "},
    {"year":"1961","event":"Establishes Central Research Laboratories."},
    {"year":"1962","event":"Establishes Sharp Electronics Corporation (SEC) in the US, the company’s first overseas sales base. Begins mass production of commercial-use microwave ovens (R-10). Osaka Municipal Hayakawa Welfare Hall completed with construction funds donated by President Hayakawa. Builds shrine on Mt. Koya for holding Buddhist memorial services for deceased employees. "},
    {"year":"1963","event":"Establishes service company in Osaka. Company reorganized into three divisions: radio, home appliances, and industrial equipment. Establishes Sharp Tokyo Product Center. "},
    {"year":"1964","event":"Release world’s first all-transistor diode electronic desktop calculator (CS-10A) as company moves to become a comprehensive electronics manufacturer. Builds mass-production line for solar cells. "},
    {"year":"1965","event":"Institutes 70 Strategy to strengthen distribution system. Launches ATOM Unit program. "},
    {"year":"1966","event":"Releases home-use microwave oven with a turntable (R-600). "},
    {"year":"1967","event":"Launches 55 Campaign that included Sharp technology fairs to celebrate 55th anniversary of company’s founding. Constructs Hiroshima Plant to mass produce transistor radios. Sharp Electric absorbed into Hayakawa Electric. Sharp Electronic Sales Okinawa Corporation established in Okinawa, then under US rule. "},
    {"year":"1968","event":"Establishes Hayakawa Electric Europe GmbH (HEEG) (name changed to Sharp Electronics [Europe] GmbH [SEEG] in 1970) as sales base in West Germany. Holds first Basic Management Policy Conference. Constructs Tochigi Plant to mass produce color TVs. Establishes Business Cooperation Centers nationwide. "},
    {"year":"1969","event":"Launches MI campaign. Signs cooperative technical agreement with North American Rockwell Corporation on ICs. Osaka Municipal Abeno Youth Center completed with construction funds donated by President Hayakawa. Establishes office equipment sales companies in Tokyo, Osaka, and Nagoya. Establishes Sharp Electronics (U.K.) Ltd. (SUK) as sales base in the UK. Develops world’s first GND (gallium arsenic negative-resistance light-emitting diode) semiconductor. Releases world’s first electronic calculator incorporating MOS LSIs (QT-8D). "},
    {"year":"1970","event":"Changes company name to Sharp Corporation. Establishes Sharp Precision Machinery Co., Ltd. (name changed to Sharp Manufacturing Systems Corporation in 1994). Senior Executive Director Akira Saeki named president, President Tokuji Hayakawa named chairman. Constructs Advanced Development and Planning Center. Implements business group system. Releases gallium arsenide double LED. "},
    {"year":"1971","event":"Establishes Sharp Corporation of Australia Pty. Ltd. (SCA) as sales base in Australia. Awarded the 1970 Okochi Memorial Production Prize for incorporating ELSIs in calculators. "},
    {"year":"1972","event":"Releases company’s first copier. Launches new sales company system (regional sales companies consolidated into 16 companies by region). Launches S734 Project for developing COS calculators. Adds Sharp Grand Award to annual employee commendation. Opens Consumer Information Centers at nine service companies throughout Japan. Establishes Sharp System Products Co., Ltd.. Forms Sharp Employee Stockholder Association. "},
    {"year":"1973","event":"Establishes Business Philosophy, Business Creed, and Basic Business Principles. Sets up employee savings scheme. Establishes Sharp Data Corporation (SDA) (name changed to Sharp Korea Corporation [SKC] in 1984) as manufacturing base in Korea. Begins production of CMOS LSIs; releases pocket-sized COS calculator with LCD. "},
    {"year":"1974","event":"Holds first company-wide QC circle convention. Constructs former Sharp Tokyo Building (Sharp Tokyo Ichigaya Building). Establishes Sharp Electronics of Canada Ltd. (SECL) as sales base in Canada. Establishes Sharp-Roxy Corporation (M) Sdn. Bhd. (SRC) as manufacturing base in Malaysia (name changed to S&O Electronics [Malaysia] Sdn. Bhd. [SOEM] in 2008). Launches ELM products. Formulates company-wide quality standards (SS: Sharp Corporation Standards). "},
    {"year":"1975","event":"Begins mass production of color TVs at SCA in Australia. "},
    {"year":"1976","event":"Launches New Life product strategy. Sharp solar cells installed on Ume, Japan’s first operational ionosphere-observing satellite. "},
    {"year":"1977","event":"Establishes Sharp System Service. Launches Special Project Team system. Tokusen Metal Limited Partnership certified as special subsidiary of Sharp Corporation. "},
    {"year":"1978","event":"Installs automated production line for the complete fabrication of calculators (awarded the Okochi Memorial Production Prize in 1981). "},
    {"year":"1979","event":"Establishes Sharp Electronics (Svenska) AB (SES) (name changed to Sharp Electronics [Nordic] AB [SEN] in 2000) as sales base in Sweden. Sharp Manufacturing Company of America (SMCA) starts operations as production division of SEC. Establishes SBC Software. "},
    {"year":"1980","event":"Announces one-trillion yen initiative. Forms Sharp Fellowship Society. Launches New Business product strategy under a “new business style” concept. Chairman Tokuji Hayakawa passes away. Establishes Sharp Business Co., Ltd.. Establishes Sharp-Roxy Electronics Corporation (M) Sdn. Bhd. (SREC) as manufacturing base in Malaysia (merged into SMM in 2009). "},
    {"year":"1981","event":"Establishes Sharp Consumer Electronics Co., Ltd.. Constructs Shinjo Plant (now Katsuragi Plant) in Nara. Constructs mass-production plant for EL displays (starts full-scale operations in 1983). Develops laser diode with VSIS architecture. "},
    {"year":"1982","event":"Establishes Sharp (Phils.) Corporation (SPC) as manufacturing base in the Philippines. Establishes Sharp Finance Corporation. Establishes Sharp-ECD Solar Co., Ltd. as joint venture with Energy Conversion Devices Inc. of the US. Sharp multinet system goes online. Tokusen Metal Limited Partnership reorganized into Sharp Tokusen Industry Co.. "},
    {"year":"1983","event":"Establishes Sharp Engineering Corporation. EL displays installed on the Space Shuttle. "},
    {"year":"1985","event":"Sharp Manufacturing Company of U.K. (SUKM) starts operations as production division of SUK. Holds comprehensive technology exhibitions in Beijing and Shanghai. Establishes Sharp-Roxy Appliances Corporation (M) Sdn. Bhd. (SRAC) as manufacturing base in Malaysia (ceases operations in 2002). Establishes Sharp-Roxy Sales & Service Company (M) Sdn. Bhd. (SRSSC) as sales base in Malaysia. Establishes Creative Lifestyle Focus Center. Constructs Fukuyama Plant. Establishes Sharp Trading Corporation. Builds prototype of 3-inch color LCD TV. "},
    {"year":"1986","event":"Builds “futuristic electric house” on the grounds of Yao Plant. Establishes Sharp Electronics (Schweiz) AG (SEZ) as sales base in Switzerland. Establishes Sharp Electronics GmbH (SEA) as sales base in Austria (merges with SEEG in 2004 to become SEEG Austria Branch). Establishes Sharp-Roxy Sales (Singapore) Pte., Ltd. (SRS) as sales base in Singapore. Establishes Sharp Electrónica España S.A. (SEES) as manufacturing and sales base in Spain (ceases manufacturing in 2011). Senior Executive Director Haruo Tsuji named president, President Akira Saeki named chairman. Establishes Sharp Electronics Taiwan Co., Ltd. (SET) as manufacturing base in Taiwan (liquidated in 2010). Launches Liquid Crystal Display Division. "},
    {"year":"1987","event":"Establishes Sharp Electronics Sales Corporation. Establishes Sharp Appliances (Thailand) Limited (SATL) as manufacturing base in Thailand. Establishes Sharp Electronics (Singapore) Pte., Ltd. (SESL) as kit export base in Singapore. Chairman Akira Saeki appointed as corporate advisor. Establishes Sharp-Roxy (Hong Kong) Ltd. (SRH) as sales base in Hong Kong. "},
    {"year":"1988","event":"The Sharp Columbus, a promotional event boat, cruises the waters of Japan for 18 months. Establishes Sharp Corporation of New Zealand Ltd. (SCNZ) as sales base in New Zealand. Establishes Sharp Precision Manufacturing (U.K.) Ltd. (SPM) as manufacturing base in the UK (liquidated in 2010). Introduces in-house recruiting system. Develops hologram laser unit jointly with Philips International B.V. of the Netherlands. Proclaims goal of becoming comprehensive electronics manufacturer on the strength of its optoelectronics technologies. Develops world’s first 14-inch color TFT LCD. "},
    {"year":"1989","event":"Establishes Sharp Manufacturing France S.A. (SMF) as manufacturing base in France. Establishes Sharp Thebnakorn Co., Ltd. (STCL) as sales base in Thailand (name changed to Sharp Thai Co., Ltd. [STCL] in 2007). Establishes Kalyani Sharp India Limited (KSIL) as manufacturing base in India (name changed to Sharp India Limited [SIL] in 2005). Establishes Sharp Manufacturing Corporation (M) Sdn. Bhd. (SMM) as manufacturing base in Malaysia. "},
    {"year":"1990","event":"Establishes Sharp Corporation (Taiwan) (SCOT) as sales base in Taiwan. Establishes Sharp Laboratories of Europe, Ltd. (SLE) as base to conduct basic research in the UK. Launches Liquid Crystal Display Group. SUKM receives the UK Queen’s Award for Export and Technology. Establishes Sharp International Finance (U.K.) Plc. (SIF) as financial subsidiary in the UK. Establishes Sharp Burotype Machines S.A. (SBM) as sales base in France (name changed to Sharp Electronics France S.A. [SEF] in 1991). Establishes Sharp Electronics (Italia) S.p.A. (SEIS) as sales base in Italy. Company-wide small-group activities renamed Sharp CATS (Creative Action Teams). Establishes childcare leave system. Achieves non-consolidated net sales of 1 trillion yen (fiscal 1989). "},
    {"year":"1991","event":"Establishes Sharp Electronics Benelux B.V. as sales base in the Netherlands. Begins production at color TFT LCD plant (NF-1 production line) at Advanced Development and Planning Center. "},
    {"year":"1992","event":"Establishes Sharp Electronic Components (Taiwan) Corporation (SECT) as electronic components sales base, and Sharp Technology (Taiwan) Co., Ltd. (STT) as IC design and development base (STT liquidated in 2007). Ties up with Intel Corporation in flash memory business. Establishes Sharp Live Electronics Sales Corporation. Establishes Shanghai Sharp Air-Conditioning Systems Co., Ltd. (SSAC) as manufacturing base in China (name changed to Shanghai Sharp Electronics Co., Ltd. [SSEC] in 1994). Constructs Makuhari Building. Establishes Sharp Thebnakorn Manufacturing (Thailand) (STTM) as production division of STCL. "},
    {"year":"1993","event":"Begins production at Fukuyama Plant using 0.6 μm process design rules. Establishes Sharp Office Equipments (Changshu) Co., Ltd. (SOCC) as manufacturing base in China. "},
    {"year":"1994","event":"Develops industry’s first reflective TFT LCD requiring no backlight. Establishes Wuxi Sharp Electronic Components Co., Ltd. (WSEC) as manufacturing base in China. Establishes P.T. Sharp Yasonta Indonesia (SYI) as manufacturing base, and P.T. Sharp Yasonta Antarnusa (SYA) as sales base in Indonesia (the two merged to form P.T. Sharp Electronics Indonesia [SEID] in 2005). "},
    {"year":"1995","event":"Establishes Sharp Laboratories of America, Inc. (SLA) as research base in the US. Establishes P.T. Sharp Semiconductor Indonesia (SSI) as manufacturing base for semiconductors in Indonesia. Begins operations at Mie Plant for mass production of LCDs. Establishes Sharp Electronics (Malaysia) Sdn. Bhd. (SEM) as combined R&D base and parts supplier in Malaysia. "},
    {"year":"1996","event":"Establishes Nanjing Sharp Electronics Co., Ltd. (NSEC) as manufacturing base in China. Official Sharp Internet website opens. "},
    {"year":"1997","event":"All Sharp production bases in Japan certified for ISO 14001. Establishes Shanghai Sharp Mold and Manufacturing Systems Co., Ltd. (SSMC) as manufacturing base in China. Establishes Sharp Electrónica Mexico S.A. de C.V. (SEMEX) as manufacturing base in Mexico. Launches Environmental Protection Group and starts 3G-1R Strategy. Introduces integrated distribution system in Japan. "},
    {"year":"1998","event":"Establishes Sharp Middle East Free Zone Establishment (SMEF) as sales base in Dubai, United Arab Emirates. Jointly develops world’s first CG-Silicon (continuous grain silicon) technology with Semiconductor Energy Laboratory Co., Ltd.. Develops and begins mass production of world’s first stacked CSP (chip size package). Establishes Sharp Document Systems Corporation and Sharp Amenity Systems Corporation. Corporate Senior Executive Director Katsuhiko Machida named president, President Haruo Tsuji named corporate advisor. Formulates Sharp Business Standards and Action Guidelines. Establishes Sharp Electronics Marketing Corporation. President Machida declares that by 2005 all TVs Sharp sells in Japan will be LCD TVs. "},
    {"year":"1999","event":"Launches Sharp Space Town information service. Develops 1-bit amplifier technology for reproducing ultra high-fidelity sound. Establishes Sharp Electronics Inc. of Korea (SEI) as sales base in Korea. Establishes Sharp Software Development India Pvt. Ltd. (SSDI) as software development company in India. Publishes first Environmental Report. "},
    {"year":"2000","event":"Launches advertising campaign for AQUOS, calling it a TV for the 21st century. Establishes Sharp Microelectronics of China (Shanghai) Co., Ltd. (SMC) as sales base in China (name changed to Sharp Electronics [Shanghai] Co., Ltd. [SES] in 2003). Establishes Sharp Business Systems (India) Limited (SBI) as sales base in India. Becomes world’s largest manufacturer of solar cells. Maintains this position for seven consecutive years, until 2006. "},
    {"year":"2001","event":"Releases TVs with Advanced Super View LCD. Establishes S.I. Solutions jointly with IBM Japan. Kansai Recycling Systems Co., Ltd. starts operations (established in 1999). Establishes Sharp Telecommunications of Europe, Ltd. (STE) as mobile telecommunications development base in the UK. Establishes usability labs. Establishes Comprehensive Call Centers (Customer Assistance Centers) for handling customer inquiries. Establishes BRM (business risk management) Committee. "},
    {"year":"2002","event":"Ties up with El-Araby Group for air conditioning business in Egypt. Operations begin at Mihara Plant. Develops 3D LCD that can be switched between 2D and 3D formats. "},
    {"year":"2003","event":"Revises Sharp Business Standards and Action Guidelines, enacts Sharp Charter of Corporate Behavior. Launches Sharp Green Club (SGC). SEMEX in Mexico begins production of AQUOS LCD TVs. Establishes consumer electronics R and D center in China. Constructs Mie Plant No. 3 to manufacture System LCDs. Changes name of small-group activities to R-CATS and starts unique activities. Establishes CSR Promotion Division. Develops reflective or transmissive Mobile Advanced Super View LCD."},
    {"year":"2004","event":"Starts eS-SEM strategic management system. Operations begin at Kameyama Plant. Establishes Sharp Technical Components (Wuxi) Co., Ltd. as manufacturing base in China. Opens AQUOS Plaza sites in Tokyo, Nagoya, and Osaka for the repair of large-screen AQUOS LCD TVs. Announces environmental vision of becoming a zero global warming impact company by 2010 (achieved in 2008). "},
    {"year":"2005","event":"Takes part in Team Minus 6%, Cool Biz, and Warm Biz, three initiatives of Japan’s Ministry of the Environment. Establishes Sharp Electronics Sales (China) Co., Ltd. (SESC) as sales base in China. Launches Sharp Yonago Corporation. Establishes Sharp Manufacturing (Thailand) Co., Ltd. (SMTL) as manufacturing base in Thailand (reorganization of STTM). Establishes Sharp Group Charter of Corporate Behavior and Sharp Code of Conduct. Electronic calculators recognized as IEEE Milestone. "},
    {"year":"2006","event":"Establishes Sharp Manufacturing Poland Sp. z o.o. (SMPL) as manufacturing base in Poland. Kameyama Plant wins the Economy, Trade and Industry Minister’s Prize in the 8th Japan Water Award. Teams up with NPO Weathercaster Network to begin eco-education in elementary schools in Japan. "},
    {"year":"2007","event":"Corporate Senior Executive Director Mikio Katayama named president; President Katsuhiko Machida named chairman. Establishes Sharp Electronics Russia LLC (SER) as sales base in Russia. SEEG split into three separate entities for consumer electronics, information products, and solar power systems. Establishes Toyama Plant to manufacture silicon for solar cells. "},
    {"year":"2008","event":"Introduces executive officer system. Establishes Health and Environment Systems Group. Sharp Corporation attains Privacy Mark certification. Announces goal of becoming a total solutions provider for solar power. "},
    {"year":"2009","event":"Establishes Sharp Electronics (Vietnam) Company Limited (SVN) as sales base in Vietnam. Announces new environmental vision of becoming an Eco-Positive Company. Starts production of LCD panels at Green Front Sakai. "},
    {"year":"2010","event":"Akira Saeki, corporate senior advisor and former president, passes away. Develops high-conversion-efficiency solar cells. Starts production of solar cells at Green Front Sakai. Solar cell business recognized as IEEE Milestone. Establishes Sharp Corporation Mexico, S.A. de C.V. (SCMEX) as sales base in Mexico. Establishes Enel Green Power & Sharp Solar Energy S.r.l. (ESSE) as independent power producer in Italy. Establishes 3 Sun S.r.l. as manufacturing base in Italy. Establishes Sharp Electronics Research & Development (Nanjing) Co., Ltd. (SERD) as design and development base in China. Acquires Recurrent Energy, LLC, a US developer of solar power plants. "},
    {"year":"2011","event":"Establishes Sharp Laboratories of China Co., Ltd. (SLC) as R&D base in China. Establishes Sharp Solar Maintenance Asia Co., Ltd. (SSMA) as maintenance company for solar power plants in Thailand. Establishes Sharp Brasil Comércio e Distribuição de Artigos Eletrônicos Ltda. (SBCD) as sales base in Brazil. Establishes Sharp (China) Investment Co., Ltd. (SCIC) as Chinese headquarters. "},
    {"year":"2012","event":"Executive Managing Officer Takashi Okuda named president; President Mikio Katayama named chairman. Starts mass production of LCD panels using IGZO (oxide semiconductor) technology. Establishes Sharp Electronics (Europe) Limited (SEE) as European headquarters in the UK. Celebrates 100th anniversary of company founding. Forms capital alliance with Qualcomm Incorporated and signs joint development agreement for next-generation MEMS displays. "},
    {"year":"2013","event":"Reorganizes Japanese domestic sales companies: establishes Sharp Business Solutions Corporation (SBS) to handle B2B sales; changes name of solar and energy-related sales company to Sharp Energy Solutions Corporation (SESJ). Strengthens alliance with Samsung Electronics Co., Ltd. in LCD business and forms capital alliance with its Japanese subsidiary Samsung Electronics Japan Co., Ltd.. Crystal Clear Solar, a joint venture of Sharp and Fuyo General Lease Co., Ltd., starts operation of solar power plants in Osaka and several other locations in Japan. Starts production of IGZO LCD panels for notebook PCs. Construction completed on solar power plant in Thailand. Executive Vice President Kozo Takashi named president; Takashi Okuda named chairman. Enters into LED and laser diode patent cross-licensing agreement with OSRAM GmbH. Starts operations of new home appliance plant in Karawang, Indonesia. Enters into collaborative partnership with Denso Corporation, forms capital alliances with Makita Corporation and Lixil Corporation, and issues new shares through third-party allotment with the three companies. Increases capital through public stock offering. "},
    {"year":"2014","event":"50th anniversary since releasing the first calculator in Japan. Develops Free-Form Display that enables the creation of new display designs to match a variety of applications. 14-Inch TFT-LCD Recognized as IEEE Milestone. Opens multipurpose space for solution proposals at ;ABENO HARUKAS (Abeno-ku, Osaka), the tallest building complex in Japan. "},
    {"year":"2015","event":"Representative Director and Executive Vice President Shigeaki Mizushima named chairman. Issuance of Class Shares by third party allotment to Mizuho Bank Ltd., The Bank of Tokyo-Mitsubishi UFJ. Ltd., and Japan Industrial Solutions. New FFD (Free Form Display) technology developed allowing designers to integrate a display of virtually any shape into their products. Crystal Clear Solar, a joint venture of Sharp and Fuyo General Lease Co., Ltd., expands operation area of solar power plants to Hokkaido and other locations in Japan. Industry first products such as AQUOS 4K NEXT' 4K LCD TV realizing 8K equivalent display, 'Healsio Hotcook' and 'DC Hybrid Air Conditioner' introduced. "},
    {"year":"2016","event":"World's first Plasmacluster Air Purifier with Mosquito catcher without using chemicals introduced to Japanese market (introduced to ASEAN market in September 2015). Announces strategic alliance with Hon Hai Precision Industry Co., Ltd.. Reassignment to 2nd Section from 1st Section of Tokyo Stock Exchange. Head office relocated from Osaka City (22-22, Nagaike-cho, Abeno-ku, Osaka City) to Sakai City (1 Takumi-cho, Sakai-ku, Sakai City). Sharp's shares of 388.8 billion yen in total subscribed to Hon Hai Precision Industry Co., Ltd. and 3 others. J.W. Tai (Executive V.P. of Hon Hai Precision Ind. Co., Ltd.) named president. "}
];
exports.handler = function(event, context, callback) {
    var alexa = Alexa.handler(event, context);
    alexa.registerHandlers(handlers);
    alexa.execute();
};

var handlers = {
    'LaunchRequest': function () {
        this.emit(":ask","You can ask year and then I will answer what happened","Say yes to continue or no to exit");
        // this.emit(":ask","welcome come here","come here");
    },
    
//     "AMAZON.YesIntent":function(){
//         // this.emit(":ask","What's date?","What's date?");
//         date.data.call(this);
//   },
  'Unhandled':function(){
      this.emit(':ask','try again','try again');
  },
   "AMAZON.NoIntent":function(){
         this.emit(":tell","OK, goodbye");
  },
  "dataIntent":function(){
      dateOne.dataTwo.call(this);
  },
  "AMAZON.StopIntent":function(){
    //  dateOne.stop.call(this
    this.emit(":tell","OK,GOOD BYE")
  },
  "AMAZON.CancelIntent":function(){
      this.emit(':tell',"ok,good bye");
  }
};
var dateOne=function(){
    return{
        dataTwo:function(){
            var intent=this.event.request.intent.slots.data.value;
            var eventOne;
            var aa;
            for(var i=0 ; i<date.length;i++){
                if(intent==date[i].year){
                    eventOne = date[i].event;
                    aa="01";
                    break;
                }
                aa = "00";
            };
            
            
            if(aa == "00"){
                eventOne ="there is no answer.";
            };
            
            
            this.emit(":ask",eventOne,"you can say other data");
        }
        
    }
}();
