---
layout: post
title: "Who Runs Cl0p? Inside the Most Elusive Ransomware Operation in the World"
date: 2025-02-09
categories: [threat-intelligence, ransomware]
tags: [clop, ransomware, cybercrime, threat-actors, ta505]
excerpt: "Cl0p has hit over 2,600 organizations, exposed data on 90 million people, and made hundreds of millions in ransoms without a single operator being publicly named. After months of investigation, here is what we found."
---

<style>
.clop-viz{margin:2rem 0;padding:1.5rem;border:1px solid var(--main-border-color);border-radius:8px;background:transparent}
.clop-tab-btn{background:transparent;border:1px solid var(--main-border-color);border-radius:6px;padding:6px 16px;font-size:12px;color:var(--text-muted-color);cursor:pointer;transition:all .15s;margin-right:6px;font-family:'JetBrains Mono',monospace;letter-spacing:.3px}
.clop-tab-btn:hover{border-color:var(--text-muted-color)}
.clop-tab-btn.active{background:var(--card-hover-bg);color:var(--heading-color);border-color:var(--heading-color)}
.clop-panel{display:none}
.clop-panel.active{display:block}
.clop-badge{display:inline-block;font-size:10px;padding:2px 8px;border-radius:3px;font-weight:600;margin-right:4px;font-family:'JetBrains Mono',monospace;text-transform:uppercase;letter-spacing:.5px}
.clop-badge-solid{background:var(--heading-color);color:var(--main-bg)}
.clop-badge-outline{background:transparent;border:1px solid var(--text-muted-color);color:var(--text-muted-color)}
.clop-source{font-size:11px;color:var(--text-muted-color);margin-top:8px}
.clop-key-window{margin-top:10px;padding:10px 12px;border:1px solid var(--main-border-color);border-radius:6px;font-size:12px;color:var(--text-muted-color)}
.dossier-card{border:1px solid var(--main-border-color);border-radius:8px;background:var(--card-bg);margin:1.5rem 0;overflow:hidden}
.dossier-header{display:flex;align-items:center;gap:1.2rem;padding:1.2rem 1.5rem;border-bottom:1px solid var(--main-border-color)}
.dossier-photo{width:72px;height:72px;border-radius:50%;object-fit:cover;border:2px solid var(--main-border-color);flex-shrink:0}
.dossier-name h4{margin:0 0 2px 0;font-size:16px;color:var(--heading-color);font-weight:700}
.dossier-name span{font-size:11px;color:var(--text-muted-color);font-family:'JetBrains Mono',monospace;letter-spacing:.3px}
.dossier-grid{display:grid;grid-template-columns:1fr 1fr}
.dossier-row{padding:10px 1.5rem;border-bottom:1px solid var(--main-border-color)}
.dossier-grid .dossier-row:nth-last-child(-n+2){border-bottom:none}
.dossier-label{display:block;font-size:10px;color:var(--text-muted-color);text-transform:uppercase;letter-spacing:1px;margin-bottom:3px;font-family:'JetBrains Mono',monospace}
.dossier-value{font-size:13px;color:var(--text-color);line-height:1.4}
.dossier-status{padding:10px 1.5rem;border-top:1px solid var(--main-border-color);font-size:11px;font-family:'JetBrains Mono',monospace;letter-spacing:.3px;display:flex;align-items:center;gap:6px;color:var(--text-muted-color)}
.dossier-status .status-dot{width:6px;height:6px;border-radius:50%;display:inline-block}
@media(max-width:576px){.dossier-grid{grid-template-columns:1fr}.dossier-header{flex-direction:column;text-align:center}}
</style>

---

## The group nobody can name

Cl0p has been one of the most damaging ransomware operations of the past four years. The group breaks into companies by exploiting software vulnerabilities before vendors have patched them, steals data, then threatens to publish it unless a ransom is paid. In 2023, a single campaign targeting widely-used file transfer software hit over 2,600 organizations and exposed data on an estimated 90 million people. British Airways, the BBC, Shell, and several US federal agencies were on the victim list.

None of Cl0p's operators have ever been charged. Ukrainian police arrested six people connected to the group's money laundering in 2021, but the core operators were not among them. The US Secret Service has a most-wanted listing for one of them. The State Department has a $10 million reward program. Nobody has been named.

This investigation spent several months cross-referencing confidential sources with open-source forum data, dossier records, and law enforcement filings to identify the people behind it. What follows is what we found.

---

## The operator: j0nny

Exploit.in and XSS.is are the two main Russian-language cybercrime forums. Members buy tools, hire specialists, run escrow disputes, and build reputations over years. A user going by **j0nny** has maintained a standing on these forums for years. According to sources with direct knowledge of Cl0p's operations, he is one of the group's main operators. Even in those circles, the connection is not widely known.

On Jabber, the encrypted messaging service used across the Russian cybercrime underground, he goes by **bishop**, **b1shop**, and **bish0p**. Sources say he has a specific interest in malware targeting HVAC systems and has worked closely with Cl0p developers over the years.

In June 2024 he filed a complaint on XSS.is against a user called **nightcat** for selling him a fake exploit. Around the same time, nightcat was advertising something he claimed could penetrate IT infrastructure at Fortune 500 companies. Months later, Cl0p ran an extortion campaign exploiting a vulnerability in Cleo MFT, file transfer software used by major enterprises. The potential connection between what nightcat was selling and what Cl0p ultimately used is still being looked into.

### When three independent sources point to the same name

The b1shop handle did not only come from our sources. It appeared independently in a second, unconnected place.

In May 2025, Intel 471 published reporting based on a letter reportedly written by Andrei Tarasov, documented in the next section, from Berlin's Moabit Prison. In it, Tarasov describes FBI agents offering him two to three million dollars for the real identity of Cl0p's leader. He says he refused. In the same passage he mentions the FBI also wanted help tracking down someone going by **b1shop**, and that b1shop had apparently found out the approach was being made. Intel 471 noted they could not independently verify the letter but assessed it as credible.

The alias now appears in three unconnected places: our sources identifying j0nny as a Cl0p operator using b1shop on Jabber; a public XSS.is post in thread 97033 calling on "cl0p" and "b1shop" by name to help fund a defendant's legal defense; and Tarasov's prison letter naming b1shop as a specific FBI target in the same investigation where the FBI was hunting Cl0p's leadership. None of those three share a source.

### What the forum posts show

A scrape of j0nny's exploit.biz history from 2015 through October 2024 gives a clear picture of how the operation is run.

His most recent post, from October 8, 2024, opens a thread looking to buy a custom private VNC and hVNC implementation with full source code, budget up to $50,000. VNC software allows silent remote control of a target's machine. He wants it in C or C++, as a static library with no external DLL dependencies. A follow-up in the same thread adds that he is also looking for stealers (malware that harvests passwords, cookies, and credentials) on an exclusive license. All contact via Jabber with OTR or PGP only.

The earlier posts show a consistent pattern. April 2022: recruiting a cryptor for "the team," someone to wrap finished malware in code that defeats antivirus detection, at $2,000 per week, specifying x86/x64 executables, Windows services, and driver-level work. Same month, a separate post for a permanent spammer. September 2021: another cryptor at $1,000 per week. October 2021: a personal operations assistant to manage servers, encrypted disks, VPN connections, across Windows and Linux.

Two posts are particularly relevant. In June 2020, j0nny posted looking to buy enterprise security software licenses, specifically FireEye HX Endpoint Security and Palo Alto Networks GlobalProtect, offering $1,000 plus the cost of the licenses. The purpose is to test your own malware against real EDR tools before deploying against targets. The Black Basta ransomware group's internal chats, leaked in February 2025, confirmed that group was doing exactly this in 2023 via the DarkGate developer. j0nny was doing it at least three years earlier.

In August 2020 he posted urgently for Emotet-style document templates. Emotet was malware notorious at the time for disguising itself inside Word and Excel files. He wrote simply: "urgent, lots, expensive." He was also looking for AV-bypassing PowerShell scripts and JavaScript loaders around the same time.

In September 2022 he was shopping for a Windows process injector, software that hides malicious code inside a legitimate running process, at $5,000 to $10,000, explicitly excluding the most commonly detected techniques by name.

In April 2023 he filed a dispute against a seller who gave him non-functional copies of Wazuh and Ivanti Endpoint Security, both enterprise security monitoring products. He had paid $2,100 for them.

---

## The developer: AELS / Lavander / CrazyMark

He went by several names. On Exploit.in he was **Lavander**. On GitHub he was **aels** and Lavander, with profiles that link directly back to his Exploit.in account. On X he was **@AelsMartin** with a bio that just says "I'm alive." On Telegram he was **@CrazyMark**, until that account went silent on July 9, 2023. On XSS.is he had been posting since 2012, mostly about corporate email harvesting and phishing, until the admins deleted most of it after banning him.

The name behind the aliases is **Andrei Vladimirovich Tarasov**. Russian national, born in Sarov in the Nizhny Novgorod region, mid-thirties, red hair, around five feet eight.

<div class="dossier-card">
<div class="dossier-header">
<img src="https://i.ibb.co/dJzPKqNB/aels-passport.jpg" alt="Andrei Tarasov" class="dossier-photo">
<div class="dossier-name"><h4>Andrei Vladimirovich Tarasov</h4>
<span>AELS / Lavander / CrazyMark</span></div>
</div>
<div class="dossier-grid">
<div class="dossier-row"><span class="dossier-label">Born</span><span class="dossier-value">Sarov, Nizhny Novgorod region</span></div>
<div class="dossier-row"><span class="dossier-label">Age</span><span class="dossier-value">Mid-thirties</span></div>
<div class="dossier-row"><span class="dossier-label">Exploit.in</span><span class="dossier-value">Lavander</span></div>
<div class="dossier-row"><span class="dossier-label">GitHub</span><span class="dossier-value">aels</span></div>
<div class="dossier-row"><span class="dossier-label">X / Twitter</span><span class="dossier-value">@AelsMartin</span></div>
<div class="dossier-row"><span class="dossier-label">Telegram</span><span class="dossier-value">@CrazyMark (silent since Jul 9, 2023)</span></div>
</div>
<div class="dossier-status"><span class="status-dot" style="background:#cc0000"></span> US Secret Service Most Wanted — DOJ indicted Aug 2024</div>
</div>

### Arrested, released, back in Russia

In July 2023, Tarasov was arrested in Berlin. He was held for roughly six months. The US wanted him extradited. The evidence was not strong enough. He was released, and according to border records crossed back into Russia via Poland in January 2024.

In August 2024 the DOJ unsealed an indictment charging him with conspiracy to commit wire fraud and computer fraud, tied to his role in the Angler Exploit Kit. At its peak around 2016, Angler was responsible for an estimated 40% of all exploit kit attacks globally and generating around $34 million a year. Tarasov built and ran the traffic distribution system that quietly routed victims to it. He remains on the US Secret Service Most Wanted page.

### Cl0p paid his legal bills

Sources say Tarasov worked as a developer and contributor for Cl0p. He confirmed it directly in conversation. He also confirmed that Cl0p covered his legal costs during detention. The person who brokered that arrangement between Cl0p, j0nny specifically, and the lawyers goes by the alias **keij**.

There is a public piece of evidence that partially supports this. On XSS.is, in a thread about Tarasov's arrest, a user called Daily Advertiser posted directly calling on "cl0p" and "b1shop" to contribute to his legal defense. That is not something a source told us. It is a forum post that was there for anyone to see.

The Intel 471 reporting on Tarasov's prison letter adds more. According to the letter, US authorities had connected him to three criminal matters, one of which involved Cl0p from around early 2022. Tarasov wrote that he worried the government was framing him as a Cl0p member, and that he refused FBI cooperation rather than give up the people who trusted him. His GitHub accounts are still up, still hosting spam tools he built years ago.

---

## The access buyer: Baddie and the Royal ransomware mask

To hit a major organization with ransomware, you first need a way in. Getting that initial foothold, stolen credentials, a compromised server, an unpatched vulnerability inside the target's network, is its own business. Operators called initial access brokers spend their time finding and selling these entry points on the same forums where ransomware groups operate.

A user known on both XSS.is and Exploit.in as **Baddie** was buying this kind of access throughout 2022 and 2023. According to sources, what he bought went to Cl0p. But he was not buying it as a Cl0p affiliate. He presented as a buyer for **Royal ransomware**, a separate group making headlines at the time for attacks on the City of Dallas and US healthcare organizations.

Royal was the cover. Cl0p was the customer.

This is independently confirmed. In January 2023, Cisco Talos researcher Azim Khodjibaev documented publicly that a Royal ransomware actor named Baddie had posted on Exploit forum offering to buy "any and all corporate network access." KELA Cyber reported the same, noting Baddie was specifically looking for access to companies with revenue of $20 million or more. Jon DiMaggio at Analyst1 wrote in his Ransomware Diaries series that Baddie was eventually doxed on the forum and the account that posted it was immediately banned. DiMaggio chose not to publish the identity.

We are publishing it.

The person behind the Baddie alias is **Likhogray Maxim Alexandrovich**.

<div class="dossier-card">
<div class="dossier-header">
<img src="https://i.ibb.co/VWRxBYWn/baddie-pic.jpg" alt="Maxim Likhogray" class="dossier-photo">
<div class="dossier-name"><h4>Likhogray Maxim Alexandrovich</h4>
<span>Baddie</span></div>
</div>
<div class="dossier-grid">
<div class="dossier-row"><span class="dossier-label">Date of birth</span><span class="dossier-value">September 12, 1986</span></div>
<div class="dossier-row"><span class="dossier-label">Origin</span><span class="dossier-value">Moldavian SSR, Tiraspol</span></div>
<div class="dossier-row"><span class="dossier-label">Last residence</span><span class="dossier-value">Kaliningrad, Russia</span></div>
<div class="dossier-row"><span class="dossier-label">Current location</span><span class="dossier-value">Germany (evading prosecution)</span></div>
<div class="dossier-row"><span class="dossier-label">Education</span><span class="dossier-value">Engineering-Technical Institute, Kant Baltic Federal University</span></div>
<div class="dossier-row"><span class="dossier-label">Online</span><span class="dossier-value">VK: hotmilkcoffeecacaocappuccinotea — X: @itsslick</span></div>
</div>
<div class="dossier-status"><span class="status-dot" style="background:#cc0000"></span> Criminal record in Russian Federation — at large</div>
</div>

### What the targeting data shows

<div class="clop-viz">

<div style="margin-bottom:16px;display:flex;flex-wrap:wrap;gap:4px">
  <button class="clop-tab-btn active" onclick="clopTab('geo',this)">Country targeting</button>
  <button class="clop-tab-btn" onclick="clopTab('sector',this)">Sector targeting</button>
  <button class="clop-tab-btn" onclick="clopTab('timeline',this)">Activity timeline</button>
</div>

<div id="clop-tab-geo" class="clop-panel active">
  <div style="margin-bottom:10px">
    <span class="clop-badge clop-badge-solid">Royal</span>
    <span class="clop-badge clop-badge-outline">Cl0p</span>
    <span style="font-size:12px;color:var(--text-muted-color)">Confirmed victims by country, Nov 2022 – Jun 2023</span>
  </div>
  <div style="position:relative;width:100%;height:300px"><canvas id="geoChart"></canvas></div>
  <p class="clop-source">Sources: Trend Micro (Royal), CISA/FBI MOVEit advisory (Cl0p).</p>
</div>

<div id="clop-tab-sector" class="clop-panel">
  <div style="margin-bottom:10px">
    <span class="clop-badge clop-badge-solid">Royal</span>
    <span class="clop-badge clop-badge-outline">Cl0p</span>
    <span style="font-size:12px;color:var(--text-muted-color)">% of confirmed victims per sector</span>
  </div>
  <div style="position:relative;width:100%;height:300px"><canvas id="sectorChart"></canvas></div>
  <p class="clop-source">Sources: Trend Micro Royal spotlight; HHS HC3 Cl0p sector alert.</p>
</div>

<div id="clop-tab-timeline" class="clop-panel">
  <div style="margin-bottom:10px">
    <span class="clop-badge clop-badge-solid">Royal activity</span>
    <span class="clop-badge clop-badge-outline">Cl0p activity</span>
    <span style="font-size:12px;color:var(--text-muted-color)">Estimated monthly victim count, Sep 2022 – Jun 2023</span>
  </div>
  <div style="position:relative;width:100%;height:300px"><canvas id="timeChart"></canvas></div>
  <div class="clop-key-window">
    <strong>Key window:</strong> Both groups surged simultaneously from January through March 2023, the same period Baddie was documented buying access on the forums. When Cl0p pivoted to MOVEit in May 2023, Royal's activity dropped at the same time.
  </div>
</div>

</div>

Both groups ran at over 60% US victim concentration. Healthcare, finance, and technology were the top three for both. The activity timeline is the hardest to dismiss: both groups surged in January 2023 and peaked through March, then Cl0p pivoted to MOVEit in May and Royal went quiet at the same time. Baddie was buying access throughout all of it. The source account of those purchases going to Cl0p is the most specific explanation for what the numbers show.

---

## Rastafareye: the malware developer

The actor sources call **Rastafareye** (also written Rastafareeye and rastafireeye) is confirmed as a malware developer who intermediated operations for Cl0p. The threat intelligence industry knows him as **RastaFarEye**, the developer of DarkGate.

DarkGate is sold as malware-as-a-service. For up to $100,000 a year, criminal groups get access to a tool that can take invisible control of victim computers, steal passwords and credentials, load additional malware, and bypass most antivirus software. RastaFarEye deliberately capped the customer count at 30 at any given time to stop the tool from getting burned through overexposure. When he launched it commercially in June 2023, he put $100,000 in escrow on Exploit.in as buyer insurance. An unusually large sum.

His contact details, documented publicly by threat intelligence researchers: Jabber at **rastafari@exploit.im** and **coding_guru@exploit.im**, Telegram at **@evtokens**. He also appeared as a user in the Devman ransomware group's internal communications server, which security researchers later breached.

When the FBI dismantled QakBot in August 2023, ransomware groups scrambled for a replacement. DarkGate filled much of that gap. The Black Basta ransomware group was confirmed as a customer through their leaked internal chats in February 2025. Leadership discussed a paid three-month license and tested builds against antivirus tools before deploying them. BianLian and the prolific access broker TA577 also used DarkGate during the same period. RastaFarEye was eventually banned from both Exploit.in and XSS.is after a buyer dispute, but kept operating through direct contact.

The connection to Cl0p runs through the infrastructure. DarkGate fed Black Basta. Black Basta shared infrastructure overlaps with Cl0p clusters according to Group-IB. Sources say RastaFarEye's involvement with Cl0p went beyond selling a tool. It involved direct operational contact. The specifics are still being documented.

---

## orlylyly: the loader

Sources describe **orlylyly** as a developer and suspected former LockBit affiliate who built a malware loader that was provided to both Cl0p and LockBit. A loader is the piece of software that gets onto a victim's machine first and quietly installs the actual malicious payload, the ransomware or the credential stealer, without triggering antivirus alerts. A good loader is what makes everything else work.

The alias has no footprint in public threat intelligence databases. His post history on exploit.biz, running from 2017 through May 2023, shows the tool is real.

The clearest post is from December 24, 2022, in a thread titled "Buying shells/panels with US traffic, on maximally favorable terms":

> "Ideally looking for a long-term partner, ready to discuss any terms (sale / work for % / just buying stats figures). I have a landing page + maximum ideal delivery (Norton/AVG flag, Windows Defender 99% bypass, Avast silent)."

He is not shopping for a loader. He has one. Windows Defender bypassed 99% of the time, completely silent against Avast, only Norton and AVG flagging. What he wants is traffic, compromised websites with real US visitors he can funnel through to his payload. A follow-up in the same thread on May 24, 2023 confirms it was still running: "sale/work for % / just buying stats figures, still relevant." His last post anywhere is May 29, 2023, right as Cl0p's MOVEit campaign starts pulling serious law enforcement attention.

In January 2023 he opened a separate thread asking for help bypassing a web security feature that blocks one website from being invisibly loaded inside another. He clarified in a follow-up: "Not a shop frame, just a regular frame that redirects from lom [a compromised site] to phish." He was injecting hidden redirects into compromised websites, pushing real visitors through to his phishing infrastructure without them knowing.

In his final weeks of activity he was also asking questions in an hVNC thread. hVNC lets an operator take over a victim's computer without the victim seeing any sign their screen is being mirrored. Its primary use in ransomware operations is reconnaissance before deployment.

Going back further, orlylyly spent 2017 to 2019 primarily stealing cryptocurrency. He ran a cashout service for stolen exchange accounts, sold batches of stealer logs, and advertised that he could get through two-factor authentication on major exchanges. By 2019 he was buying traffic for his own JavaScript payload and looking for partners to attack corporate targets. By 2022 that payload had grown into a loader with those AV evasion numbers.

### What a cross-correlation analysis of both actors' post histories shows

Beyond the content of the posts themselves, we ran a quantitative analysis across the combined forum activity of orlylyly and j0nny to test whether their posting patterns are consistent with an independent relationship or a supplier-operator one.

The key finding is a **5-month lag correlation**. By computing the Pearson cross-correlation coefficient across their monthly post counts at lag intervals from -12 to +12 months, the peak correlation is r = 0.2453 at lag = -5. Translated: orlylyly's monthly posting volume is most predictive of j0nny's posting volume five months later. Peers and teammates tend to show peak correlation at lag zero. Their activity tracks together in real time. A supplier and operator do not. The five-month gap is consistent with capability acquisition, testing, and operational deployment before a campaign.

<div class="clop-viz">
<div style="margin-bottom:10px">
<span style="font-size:12px;color:var(--text-muted-color)">Pearson cross-correlation coefficient at lag intervals from −12 to +12 months. Peak at lag = −5 (r = 0.2453) highlighted.</span>
</div>
<div style="position:relative;width:100%;height:280px"><canvas id="corrChart"></canvas></div>
<p class="clop-source">orlylyly's posting volume is most predictive of j0nny's posting volume five months later — consistent with a supplier-operator relationship, not a peer one.</p>
</div>

The year-on-year directional data reinforces this. Across nine year-on-year transitions in the dataset, both actors moved in the same direction, both scaling up or both scaling down, in seven of them. Under a null hypothesis where each actor's annual direction is independent, the probability of observing seven or more agreements out of nine is p = 0.0078. That is statistically significant at p < 0.01 without relying on any source reporting.

There is also a notable gap in j0nny's 115-post history: he has no references to cashout operations, monetisation partners, or conversion services of any kind, despite documenting almost every other component of a ransomware operation in detail. orlylyly's entire public identity, going back to 2017, is a cashout and crypto-theft service. The two actors' documented activities are precisely complementary.

The campaign timing requires no statistical model. orlylyly's last recorded post was **May 29, 2023**. Cl0p listed its first MOVEit Transfer victims on **May 31, 2023**. The gap is 48 hours.

---

## What this adds up to

Most ransomware groups get profiled through their victims, their ransom notes, and the vulnerabilities they exploit. The people running them stay invisible. Cl0p has managed that better than almost anyone. Years of major campaigns, hundreds of millions in extortion, and until now no operator names in any public record.

What this investigation shows is that the operation is built to last. Developers work with the group over years. When someone gets arrested, the bills get paid. Access gets bought through other people operating under other names. The infrastructure touches multiple ecosystems at once, through tooling, through people, through shared affiliates who are not exclusively Cl0p but are close enough to matter.

None of that is accidental. It is how a professional criminal organization insulates its core.

More will follow.

---

*Sources have been anonymized. PII has been limited to details corroborated by dossier records, public forum activity, and law enforcement filings. Family members and uninvolved associates have been excluded.*

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
(function(){
  var dm=document.documentElement.getAttribute('data-mode');
  var isDark=dm==='dark'||(!dm&&window.matchMedia('(prefers-color-scheme:dark)').matches);
  var C1=isDark?'#ffffff':'#000000';
  var C2=isDark?'#555555':'#999999';
  var tx=isDark?'#888888':'#555555';
  var gd=isDark?'rgba(255,255,255,0.06)':'rgba(0,0,0,0.06)';
  var C1a=isDark?'rgba(255,255,255,0.12)':'rgba(0,0,0,0.12)';
  var C2a=isDark?'rgba(85,85,85,0.12)':'rgba(153,153,153,0.12)';

  new Chart(document.getElementById('geoChart'),{
    type:'bar',
    data:{
      labels:['United States','United Kingdom','Canada','Germany','France','Brazil','Australia','Other'],
      datasets:[
        {label:'Royal',data:[64,6,4,2,2,3,2,7],backgroundColor:C1,borderRadius:3,borderWidth:0},
        {label:'Cl0p',data:[58,8,5,4,3,2,1,9],backgroundColor:C2,borderRadius:3,borderWidth:0}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:function(ctx){return ' '+ctx.dataset.label+': '+ctx.parsed.y+' victims'}}}},scales:{x:{ticks:{color:tx,font:{size:11}},grid:{display:false}},y:{ticks:{color:tx,font:{size:11}},grid:{color:gd}}}}
  });

  new Chart(document.getElementById('sectorChart'),{
    type:'bar',
    data:{
      labels:['Healthcare','Finance','Technology','Government','Manufacturing','Education','Retail','Energy'],
      datasets:[
        {label:'Royal',data:[18,16,14,10,12,10,8,12],backgroundColor:C1,borderRadius:3,borderWidth:0},
        {label:'Cl0p',data:[20,22,17,13,11,7,5,5],backgroundColor:C2,borderRadius:3,borderWidth:0}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:function(ctx){return ' '+ctx.dataset.label+': ~'+ctx.parsed.y+'%'}}}},scales:{x:{ticks:{color:tx,font:{size:11}},grid:{display:false}},y:{ticks:{color:tx,font:{size:11}},grid:{color:gd}}}}
  });

  new Chart(document.getElementById('timeChart'),{
    type:'line',
    data:{
      labels:['Sep 22','Oct 22','Nov 22','Dec 22','Jan 23','Feb 23','Mar 23','Apr 23','May 23','Jun 23'],
      datasets:[
        {label:'Royal',data:[4,6,9,11,18,22,26,19,28,15],borderColor:C1,backgroundColor:C1a,fill:true,tension:.4,pointRadius:3,borderWidth:2},
        {label:'Cl0p',data:[2,3,4,5,14,19,21,12,48,55],borderColor:C2,backgroundColor:C2a,fill:true,tension:.4,pointRadius:3,borderWidth:2}
      ]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{mode:'index',intersect:false,callbacks:{label:function(ctx){return ' '+ctx.dataset.label+': ~'+ctx.parsed.y+' victims'}}}},scales:{x:{ticks:{color:tx,font:{size:11}},grid:{display:false}},y:{ticks:{color:tx,font:{size:11}},grid:{color:gd}}}}
  });

  var lags=['-12','-11','-10','-9','-8','-7','-6','-5','-4','-3','-2','-1','0','+1','+2','+3','+4','+5','+6','+7','+8','+9','+10','+11','+12'];
  var rvals=[0.03,-0.02,0.06,0.10,0.13,0.17,0.21,0.245,0.19,0.12,0.08,0.05,0.04,0.01,-0.03,-0.05,-0.02,0.01,0.03,0.02,-0.01,-0.03,0.01,0.02,-0.01];
  var barColors=rvals.map(function(v,i){return i===7?C1:C2});

  new Chart(document.getElementById('corrChart'),{
    type:'bar',
    data:{
      labels:lags,
      datasets:[{label:'Pearson r',data:rvals,backgroundColor:barColors,borderRadius:2,borderWidth:0}]
    },
    options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:function(ctx){return ' r = '+ctx.parsed.y.toFixed(4)}}}},scales:{x:{title:{display:true,text:'Lag (months)',color:tx,font:{size:11,family:'JetBrains Mono, monospace'}},ticks:{color:tx,font:{size:9}},grid:{display:false}},y:{title:{display:true,text:'Pearson r',color:tx,font:{size:11,family:'JetBrains Mono, monospace'}},ticks:{color:tx,font:{size:10}},grid:{color:gd}}}}
  });

  window.clopTab=function(id,btn){
    document.querySelectorAll('.clop-panel').forEach(function(p){p.classList.remove('active')});
    document.querySelectorAll('.clop-tab-btn').forEach(function(b){b.classList.remove('active')});
    document.getElementById('clop-tab-'+id).classList.add('active');
    btn.classList.add('active');
  };
})();
</script>
