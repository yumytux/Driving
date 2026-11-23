# DIY coding options for CarPlay / Android Auto maps or navigation in the VW Digital Cockpit (Golf Mk8 / Mk8.5, MIB3 / MIB4)

Research date: 23 Nov 2026. Method limitation: in this session only web search result snippets were available. Every attempt to open a full page failed with DNS/network blocks (vag-coding.net, vwroc.com, forum.obdeleven.com, obdeleven.com, vwcoding.ru, blog.zsec.uk, basilfx.github.io). Findings below rest on search-engine summaries of those pages, not on full-text reads. Exact adaptation values and post dates should be checked on the pages before anyone relies on them.

## Q1: What OBDeleven / VCDS codings exist for "map in cluster" / "navigation in AID" on Golf 8 / 8.5 (5F, 17, 19), and do they cover CarPlay?

### Takeaway
The known coding is for the car's own built-in (MIB3 Discover Pro) navigation map. It shows that map in the AID, or in the AID and the centre screen at once. It is done in module 5F under the adaptation group `Dashboard_Display_Configuration`, with channels such as `ability_switch_nav_maps` and `navigation_map_resolution`. No coding was found that moves a CarPlay or Android Auto map into the cluster on a Golf 8 or 8.5. OBDeleven one-click apps cover "Navigation/Compass in Dashboard" and "Virtual Cockpit Layout", not phone maps.

### Cited Findings
- VAG Coding's Golf 8 (5H) guide is called "Virtual Cockpit and MIB3 navigation map". Its stated purpose is to display the navigation map on both the Virtual Cockpit (AID) and the MIB3. It works with VCDS, ODIS or OBDeleven in control unit 5F, adaptation `Dashboard_Display_Configuration`, including `ability_switch_nav_maps` and `navigation_map_resolution`. — [VAG Coding Golf 8 guide](https://www.vag-coding.net/vw/golf-8-5h/golf-8-5h-virtual-cockpit-and-mib3-navigation-map/) (search snippet only)
- In OBDeleven forum threads, Golf 8 owners describe 5F settings such as map transmission mode and "Ability switch nav maps" = yes. They say the cockpit map option can stay greyed out until these are set. A Caddy owner got maps in the cluster after this coding, but noted the navigation itself had to be bought via We Connect, so the coding alone did not provide navigation. — [OBDeleven forum: Navigation on cluster](https://forum.obdeleven.com/thread/13838/navigation-on-cluster-cockpit); [OBDeleven forum: Maps on virtual cockpit](https://forum.obdeleven.com/thread/12156/maps-on-virtual-cockpit?page=1) (search snippets)
- A 2021 OBDeleven forum answer said maps on the virtual cockpit were "not possible". This predates the later coding guides. — [OBDeleven forum thread 12530](https://forum.obdeleven.com/thread/12530/maps-on-virtual-cockpit) (search snippet; the date is the search engine's characterisation)
- OBDeleven's Golf 2020–2024 one-click app page lists "Navigation/Compass in Dashboard" and "Virtual Cockpit Layout", and notes that the apps depend on the car's equipment. No "CarPlay in cockpit" app was found. — [OBDeleven Golf 2020–2024 customizations](https://obdeleven.com/customizations/volkswagen/golf/2020-2024); see also [VAG Coding OBDeleven one-click list Golf 8](https://www.vag-coding.net/tutorials-information/obdeleven-one-click-apps-list/list-obdeleven-one-click-apps-golf-8-5h/)
- On a Golf 8 R (VWROC thread "Golf MK8 R dual map display – coding"), a user reported maps on both screens after the 5F change and an infotainment restart. Another poster said that when CarPlay is navigating, the cluster map they see is the native map, and that they needed a separate "hack" to keep the cluster map during CarPlay navigation. — [VWROC thread p.2](https://www.vwroc.com/forums/topic/40610-golf-mk8-r-dual-map-display-coding/page/2/) (search snippet; the "hack" was not identified)
- A French Golf 8 forum notes that native map behaviour depends on production date. Earlier cars show the map on the centre screen only. Later cars can show it on the centre screen or the cockpit. Newer cars with the right hardware can show it on both. — [Forum Golf 8 (FR) OBDeleven thread](https://www.forumgolf8.fr/forum/viewtopic.php?t=7101&start=140)
- vwcoding.ru's MQB-Evo AID page lists cluster codings such as `navigation_compass`, tested on cluster software 3470, with SFD status "unknown". — [vwcoding.ru AID](https://vwcoding.ru/en/MQB-Evo/AID/) (search snippet)
- On another VW model, a VW Vortex owner reported that the cockpit's native map switches off automatically when CarPlay navigation is active, and found nothing in OBDeleven to change this. — [VW Vortex thread](https://www.vwvortex.com/threads/anyway-to-display-nav-map-on-the-digital-cockpit-and-use-carplay-to-naviigate-at-the-same-time.9279971/)

### Inferences
- The "map in cluster" coding is a 5F feature for the native nav map. It needs factory navigation (Discover Pro / navigation licence) and does not touch the CarPlay or Android Auto video stream.
- No module 17 (dash) or 19 (gateway) channel for CarPlay map projection was found in any source.

### Gaps
- Exact channel values (for example the map transmission mode enum) could not be verified because the full pages were blocked.
- Whether a UK Golf 8.5 Style MIB4 unit even exposes `Dashboard_Display_Configuration` / `ability_switch_nav_maps` is unverified. All the sources describe MIB3 Golf 8.

## Q2: Did MIB3 Golf 8 owners get CarPlay maps in the cluster via coding? What about MIB4 (Golf 8.5, Tiguan Mk3, Passat B9)?

### Takeaway
No. No source shows a full CarPlay or Android Auto map in the AID of a Golf 8 (MIB3) or any MIB4 car through coding. The working "phone map on the cluster" mods (mib-cluster-map, mst2-cluster-nav, MIB-Addon-Cluster-AA-CP) are firmware or software patches for Harman MIB2/MIB2.5 units only, as used in Golf 7/7.5 and Tiguan AD1. On MIB4 the only map in the cockpit is VW's own navigation map.

### Cited Findings
- mib-cluster-map puts the phone's map on the digital cluster "of VW-group cars with a Harman MIB2/MIB2.5". It installs from an SD card as a software update. Release v1.2.6 (16 Nov, year as shown on GitHub) added more units, and the project lists the Golf GTE and Tiguan. — [MacsInSpace/mib-cluster-map](https://github.com/MacsInSpace/mib-cluster-map); [v1.2.6 release](https://github.com/MacsInSpace/mib-cluster-map/releases/tag/v1.2.6)
- mst2-cluster-nav shows CarPlay maps live on AID10 clusters and needs "cluster map over MOST" enabled. Its v1.0.0 release was verified only on an MIB2 Standard nav unit, and the installer refuses other HMI builds. — [perkthefox/mst2-cluster-nav](https://github.com/perkthefox/mst2-cluster-nav); [EmilGeorgievIT release v1.0.0](https://github.com/EmilGeorgievIT/mst2-cluster-nav/releases/tag/v1.0.0)
- MIB-Addon-Cluster-AA-CP adds the Android Auto and CarPlay map to the Virtual Cockpit on Tiguan AD1 and Golf 7.5 (AID10 / AID12.3, MHI2 / MIB2.5 High), run from the M.I.B. toolbox. — [ALeXXBody/MIB-Addon-Cluster-AA-CP](https://github.com/ALeXXBody/MIB-Addon-Cluster-AA-CP)
- A Sept 2025 blog on an e-Golf (MIB2) used the MIB2 Toolbox option "Ignore navigation status from smartphone" to get CarPlay navigation and AID navigation working together. — [basilfx project-egolf, 8 Sep 2025](https://basilfx.github.io/project-egolf/2025/09/08/carplay-navigation-and-aid-navigation.html) (search snippet)
- A 2026 blog on enabling CarPlay on VW/Audi says that on MIB3, turn-by-turn in the cluster is only available through the maker's own software, and that there is no free method for MIB3. — [zsec blog, "Enabling CarPlay and Android Auto for free on VW/Audi 2026"](https://blog.zsec.uk/audi-carplay-2026/) (search snippet; table partly cut off)
- On the 2025 refresh (Mk8.5), a VW Vortex poster says only VW's built-in maps appear on the cluster, not Waze, Google Maps or Apple Maps. The same author was unsure whether later 8.5 software changed this. — [VW Vortex: Maps in digital cockpit](https://www.vwvortex.com/threads/maps-in-digital-cockpit.9575873/)
- VW's Passat B9 (MIB4) material lists a Digital Cockpit Pro "Navigation" view showing the map with route guidance. This is native navigation. — [VW newsroom, Passat connected driving](https://www.volkswagen-newsroom.com/en/the-new-passat-international-media-drive-18257/connected-driving-new-cockpit-landscape-offers-intuitive-operation-18265)
- A French retailer claims its wireless CarPlay interface works with Digital Cockpit Pro on Passat B9 and Tiguan facelift. This is unverified marketing. — [hightech-privee](https://www.hightech-privee.com/interface-android-auto-apple-carplay/volkswagen/)

### Inferences
- MIB3 and MIB4 are different platforms from the Harman MIB2 units the community mods target. Nothing suggests these mods port over.
- For a 2025 Golf 8.5 Style, any full phone map in the cockpit would need VW firmware support, not coding.

### Gaps
- No Reddit (r/GolfMK8, r/GolfGTI, r/Volkswagen, r/OBDeleven), golfmk8.com or ukgolfmk8 threads came back in searches, and fetching was blocked.
- No YouTube titles claiming "CarPlay map in cockpit Golf 8.5" were found.
- Nothing found from mhhauto.

## Q3: How does SFD2 affect coding on MIB4 / Golf 8.5? Do OBDeleven, VCDS or Carista support SFD2, and at what cost?

### Takeaway
Golf 8.5 (MY2025, and per one source Golf 8 builds from about April 2024) uses SFD2. Every write needs a per-operation token from VW. As of late 2026, OBDeleven and VCDS do not unlock SFD2. Carista says it does, with VW Group authorisation, but only on its own hardware with a subscription, and this is unverified by independent sources. ODIS with online VW access remains the reliable route. Even with a full unlock, there is no known CarPlay-to-cluster coding to apply.

### Cited Findings
- vwcoding.ru lists Golf 8 from April 2024 as SFD2, says each write operation requires its own token, and advises confirming SFD2 support for the VIN before buying a tool. — [vwcoding.ru SFD](https://vwcoding.ru/en/sfd/) (search snippet)
- OBDeleven's explainer says it is "actively working" on an SFD2 unlock that depends on VW Group authorisation, with no timeline. Its FAQ says SFD2 support is "much more limited" and that vehicle, ECU and feature compatibility must be checked. — [OBDeleven: What is SFD2 unlock?](https://obdeleven.com/what-is-sfd2-unlock)
- OBDeleven forum threads on the Golf 8.5 report very limited changes are possible. Read and scan and some backups work, but writing is restricted. An April 2026 user noted Carista advertising an SFD2 unlock "with the help of Volkswagen". — [OBDeleven forum: VW Golf 8.5 SFD 2](https://forum.obdeleven.com/thread/41450/vw-golf-8-5-sfd); [Not working on MK8.5](https://forum.obdeleven.com/thread/22665/working-on-mk8-5); [SFD2 unlocked for 2024 models, p.12](https://forum.obdeleven.com/thread/20229/sfd-2-unlocked-2024-models?page=12)
- Carista says it is the first solution to unlock SFD2, with official VW Group authorisation, covering 2024+ VW/Audi/Škoda/SEAT/CUPRA. The blog shows Oct 2026 and Apr 2026 dates. — [Carista: SFD2 unlock explained](https://carista.com/blogs/news/sfd2-unlock-explained); [Carista: SFD vs SFD2](https://carista.com/blogs/news/volkswagen-sfd-vs-sfd2-differences)
- Carista's help centre says SFD/SFD2 unlock works only with official Carista adapters and is a premium feature needing an active subscription. Exact price not captured. — [Carista help: hardware](https://help.carista.com/hc/en-us/articles/360009856159-What-hardware-do-I-need-to-use-Carista-App)
- A German tool retailer (Oct 2026) says SFD2 is currently only possible via VW's own online access and its tools cannot do it. — [ml24shop](https://ml24shop.de/en-us/blogs/news/vag-sfd-unlock-sfd2-scan-tool)
- Ross-Tech sells an annual SFD (v1) unlock service, which needs HEX-NET or HEX-V2, VCDS registration and photo ID, and gives temporary unlocks. Its store page says functions locked with SFD2 are "not yet available". — [Ross-Tech SFD Unlock Service](https://store.ross-tech.com/shop/sfd_service/); [Ross-Tech Wiki: SFD](https://wiki.ross-tech.com/wiki/index.php/SFD)
- Forum posts say SFD2 started with the Mk8.5 (MY2025) in the US. They also say VCDS and third-party dongles cannot reliably get SFD2 tokens and recommend ODIS Service online with a VW subscription. — [VW Vortex: SFD (v1) for 2024 GTI](https://www.vwvortex.com/threads/sfd-version-1-for-2024-gti.9584799/); [VWROC: HEX-V2 VCDS on a Mk8.5 Golf R](https://www.vwroc.com/forums/topic/46691-hex-v2-vcds-on-a-mk85-golf-r/)

### Inferences
- For a UK 2025 Golf 8.5, OBDeleven and VCDS are effectively read-only on SFD2-protected modules such as 5F and 17. Carista is the only consumer tool claiming SFD2 writes, and only for whatever features Carista exposes. No source shows Carista offering a "CarPlay map in cockpit" feature.

### Gaps
- Which Golf 8.5 modules are SFD2 (versus SFD1 or unprotected) was not confirmed for the UK market.
- Carista's subscription price for SFD2 was not captured.

## Q4: Is the capability firmware-dependent rather than coding?

### Takeaway
Yes, the evidence points to firmware and the phone app. The turn-by-turn prompts in the cluster appeared or changed after VW software updates, and they only work with Apple Maps, which uses CarPlay's instrument cluster / secondary stream. A full CarPlay map in the cluster would need VW head unit and cluster firmware that supports CarPlay's cluster video stream. No source shows VW shipping that on Golf 8.5 MIB4 as of Nov 2026.

### Cited Findings
- German Golf 8 owners (motor-talk) report that CarPlay navigation prompts appeared in the cockpit after a software update, or after a service and settings reset, and could not be switched off. They appear with Apple Maps but not with Google Maps via CarPlay. — [motor-talk: CarPlay Navi Hinweis im Cockpit nach Update](https://www.motor-talk.de/forum/carplay-navi-hinweis-im-cockpit-nach-update-t7302368.html); [page 2](https://www.motor-talk.de/forum/carplay-navi-hinweis-im-cockpit-nach-update-t7302368.html?page=1)
- An Apple developer forum post says Apple Maps is the only navigation app using the second instrument-cluster stream. It says Apple's CarPlay documentation (updated March 2024) indicates plans to open HUD and cluster services to third-party apps. — [Apple Developer Forums thread 740100](https://developer.apple.com/forums/thread/740100)
- On BMW (not VW), CarPlay map in the cluster works only with Apple Maps. This shows the feature is an OEM firmware integration of Apple's cluster stream. — [Bimmerpost G05](https://g05.bimmerpost.com/forums/showthread.php?t=2062634)
- VW Vortex threads on 2024/2025 GTI and Golf 8.5: Waze directions did not appear on the HUD or cluster, while Apple Maps did. One OP said the cluster would not show Apple Maps itself, only turn directions in a secondary section. Reports conflict. — [VW Vortex: Waze in dash display in Golf 8.5](https://www.vwvortex.com/threads/waze-in-dash-display-in-golf-8-5.9571380/); [Apple Maps & Directions display question](https://www.vwvortex.com/threads/apple-maps-directions-display-question.9538435/)

### Inferences
- The "arrows in cockpit" on Golf 8/8.5 is a firmware feature tied to Apple Maps. Dealer software updates are what change it, not OBDeleven coding.
- If VW ever adds a full CarPlay cluster map on MIB4, it would most likely arrive as a head unit / OTA update.

### Gaps
- No VW release notes or MIB4 software train numbers tied to CarPlay cluster features were found.
- Whether iOS 26 or "CarPlay Ultra" support is coming to VW is not covered by these sources.

## Q5: Success/failure reports, side effects, reverting; arrows vs full map

### Takeaway
"Success" with coding on Golf 8 means the native map in the cockpit, sometimes on both screens. Owners report that this native cluster map can switch off while CarPlay navigation runs. CarPlay turn-by-turn arrows in the cockpit (Apple Maps only) are a firmware behaviour on some software levels. A full CarPlay or Android Auto map in the cockpit has only been achieved on MIB2/MIB2.5 cars with community firmware patches.

### Cited Findings
- Native-map coding success on Golf 8 R (both screens) after a 5F change plus infotainment reboot. Another poster needed an extra "hack" to keep the cluster map during CarPlay navigation. — [VWROC](https://www.vwroc.com/forums/topic/40610-golf-mk8-r-dual-map-display-coding/page/2/)
- The cockpit's native map switches off when CarPlay navigation is active, and nothing in OBDeleven was found to stop it. — [VW Vortex](https://www.vwvortex.com/threads/anyway-to-display-nav-map-on-the-digital-cockpit-and-use-carplay-to-naviigate-at-the-same-time.9279971/)
- A related Audi thread covers removing the Virtual Cockpit compass that shows during CarPlay or Android Auto, which illustrates cluster-side side effects. — [Audizine](https://www.audizine.com/threads/for-anyone-wanting-to-get-rid-of-virtual-cockpit-compass-w-carplay-android-auto.976833/)
- Arrows vs map in MIB2 mods: mib-cluster-map shows the CarPlay map live, but turn arrows, distance and track work with Android Auto rather than CarPlay on some units. mst2-cluster-nav says native arrows and lanes work with CarPlay on any coding. One Golf 7.5 user reported Google Maps not appearing after v1.2.4, fixed via a route-hiding setting. — [mib-cluster-map](https://github.com/MacsInSpace/mib-cluster-map); [mst2-cluster-nav](https://github.com/perkthefox/mst2-cluster-nav); [mib-cluster-map issue #100](https://github.com/MacsInSpace/mib-cluster-map/issues/100)
- Coding caution: back up coding before writing. The one-click "Navigation/Compass in Dashboard" option may give guidance or compass only, not a full map. — [OBDeleven Golf customizations](https://obdeleven.com/customizations/volkswagen/golf/2020-2024) (search summary)

### Inferences
- For a 2025 UK Golf 8.5 Style (MIB4): the realistic best case is Apple Maps turn prompts in the cockpit (firmware, dependent on software level) plus VW's native map in the cockpit if the car has factory navigation. A CarPlay full map in the cockpit has no known DIY route.
- Reverting a 5F adaptation is a matter of restoring the backed-up value. Under SFD2, even reverting needs an SFD2-capable tool or a dealer.

### Gaps
- No owner reports were found of anyone attempting (and succeeding or bricking) CarPlay-map coding on MIB4.
- Long-term side effects of the 5F map coding (for example after OTA updates resetting coding) were not documented in the snippets.
