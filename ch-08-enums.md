## Перечисления

### Описание
Продолжим наши исследования структур данных, которые нам предлагает использовать в своих программах стандартная библиотека Rust. 
Рассмотрим `перечисление` - `enum`. Это структура весьма удобна, когда необходимо упорядочить и упростить работу с конечным списком
константных значений. Например (возьмем не игрушечный пример, а близкий к реальному, чтобы вы эмоционально почувствовали необходимость 
в enum):

```rust
// Много в России городов

fn main() {
    {
        const MOSCOW: u16 = 1;
        const SAINT_PETERSBURG: u16 = 2;
        const NOVOSIBIRSK: u16 = 3;
        const YEKATERINBURG: u16 = 4;
        const NIZHNY_NOVGOROD: u16 = 5;
        const KAZAN: u16 = 6;
        const CHELYABINSK: u16 = 7;
        const OMSK: u16 = 8;
        const SAMARA: u16 = 9;
        const ROSTOV_ON_DON: u16 = 10;
        const UFA: u16 = 11;
        const KRASNOYARSK: u16 = 12;
        const PERM: u16 = 13;
        const VORONEZH: u16 = 14;
        const VOLGOGRAD: u16 = 15;
        const KRASNODAR: u16 = 16;
        const SARATOV: u16 = 17;
        const TYUMEN: u16 = 18;
        const TOLYATTI: u16 = 19;
        const IZHEVSK: u16 = 20;
        const BARNAUL: u16 = 21;
        const ULYANOVSK: u16 = 22;
        const IRKUTSK: u16 = 23;
        const KHABAROVSK: u16 = 24;
        const YAROSLAVL: u16 = 25;
        const VLADIVOSTOK: u16 = 26;
        const MAKHACHKALA: u16 = 27;
        const TOMSK: u16 = 28;
        const ORENBURG: u16 = 29;
        const KEMEROVO: u16 = 30;
        const NOVOKUZNETSK: u16 = 31;
        const RYAZAN: u16 = 32;
        const ASTRAKHAN: u16 = 33;
        const NABEREZHNYE_CHELNY: u16 = 34;
        const PENZA: u16 = 35;
        const LIPETSK: u16 = 36;
        const KIROV: u16 = 37;
        const CHEBOKSARY: u16 = 38;
        const TULA: u16 = 39;
        const KALININGRAD: u16 = 40;
        const BALASHIKHA: u16 = 41;
        const KURSK: u16 = 42;
        const STAVROPOL: u16 = 43;
        const ULAN_UDE: u16 = 44;
        const TVER: u16 = 45;
        const MAGNITOGORSK: u16 = 46;
        const SOCHI: u16 = 47;
        const IVANOVO: u16 = 48;
        const BRYANSK: u16 = 49;
        const BELGOROD: u16 = 50;
        const SURGUT: u16 = 51;
        const VLADIMIR: u16 = 52;
        const NIZHNY_TAGIL: u16 = 53;
        const ARKHANGELSK: u16 = 54;
        const CHITA: u16 = 55;
        const KALUGA: u16 = 56;
        const SMOLENSK: u16 = 57;
        const VOLZHSKY: u16 = 58;
        const KURGAN: u16 = 59;
        const CHEREPOVETS: u16 = 60;
        const ORYOL: u16 = 61;
        const SARANSK: u16 = 62;
        const VOLOGDA: u16 = 63;
        const YAKUTSK: u16 = 64;
        const VLADIKAVKAZ: u16 = 65;
        const PODOLSK: u16 = 66;
        const MURMANSK: u16 = 67;
        const GROZNY: u16 = 68;
        const TAMBOV: u16 = 69;
        const STERLITAMAK: u16 = 70;
        const PETROZAVODSK: u16 = 71;
        const KOSTROMA: u16 = 72;
        const NIZHNEVARTOVSK: u16 = 73;
        const NOVOROSSIYSK: u16 = 74;
        const YOSHKAR_OLA: u16 = 75;
        const TAGANROG: u16 = 76;
        const KOMSOMOLSK_ON_AMUR: u16 = 77;
        const KHIMKI: u16 = 78;
        const SYKTYVKAR: u16 = 79;
        const NALCHIK: u16 = 80;
        const NIZHNEKAMSK: u16 = 81;
        const SHAKHTY: u16 = 82;
        const DZERZHINSK: u16 = 83;
        const BRATSK: u16 = 84;
        const ORSK: u16 = 85;
        const ANGARSK: u16 = 86;
        const ENGELS: u16 = 87;
        const BLAGOVESHCHENSK: u16 = 88;
        const STARY_OSKOL: u16 = 89;
        const VELIKY_NOVGOROD: u16 = 90;
        const KOROLYOV: u16 = 91;
        const PSKOV: u16 = 92;
        const MYTISHCHI: u16 = 93;
        const BIYSK: u16 = 94;
        const LYUBERTSY: u16 = 95;
        const PROKOPYEVSK: u16 = 96;
        const YUZHNO_SAKHALINSK: u16 = 97;
        const BALAKOVO: u16 = 98;
        const ARMAVIR: u16 = 99;
        const RYBINSK: u16 = 100;
        const SEVERODVINSK: u16 = 101;
        const ABAKAN: u16 = 102;
        const PETROPAVLOVSK_KAMCHATSKY: u16 = 103;
        const NORILSK: u16 = 104;
        const SYZRAN: u16 = 105;
        const VOLGODONSK: u16 = 106;
        const USSURIYSK: u16 = 107;
        const KAMENSK_URALSKY: u16 = 108;
        const NOVOCHERKASSK: u16 = 109;
        const ZLATOUST: u16 = 110;
        const ELEKTROSTAL: u16 = 111;
        const ALMETYEVSK: u16 = 112;
        const KRASNOGORSK: u16 = 113;
        const SALAVAT: u16 = 114;
        const MIASS: u16 = 115;
        const NAKHODKA: u16 = 116;
        const KOPEYSK: u16 = 117;
        const PYATIGORSK: u16 = 118;
        const RUBTSOVSK: u16 = 119;
        const BEREZNIKI: u16 = 120;
        const KOLOMNA: u16 = 121;
        const MAYKOP: u16 = 122;
        const ODINTSOVO: u16 = 123;
        const KHASAVYURT: u16 = 124;
        const KOVROV: u16 = 125;
        const KISLOVODSK: u16 = 126;
        const NEFTEKAMSK: u16 = 127;
        const NEFTEYUGANSK: u16 = 128;
        const NOVOCHEBOKSARSK: u16 = 129;
        const SERPUKHOV: u16 = 130;
        const SHCHYOLKOVO: u16 = 131;
        const NOVOMOSKOVSK: u16 = 132;
        const BATAYSK: u16 = 133;
        const PERVOURALSK: u16 = 134;
        const DOMODEDOVO: u16 = 135;
        const DERBENT: u16 = 136;
        const CHERKESSK: u16 = 137;
        const OREKHOVO_ZUYEVO: u16 = 138;
        const NEVINNOMYSSK: u16 = 139;
        const DIMITROVGRAD: u16 = 140;
        const NAZRAN: u16 = 141;
        const KYZYL: u16 = 142;
        const OKTYABRSKY: u16 = 143;
        const OBNINSK: u16 = 144;
        const KASPIYSK: u16 = 145;
        const NOVY_URENGOY: u16 = 146;
        const RAMENSKOYE: u16 = 147;
        const KAMYSHIN: u16 = 148;
        const MUROM: u16 = 149;
        const ZHUKOVSKY: u16 = 150;
        const NOVOSHAKHTINSK: u16 = 151;
        const SEVERSK: u16 = 152;
        const YESSENTUKI: u16 = 153;
        const NOYABRSK: u16 = 154;
        const ARTYOM: u16 = 155;
        const PUSHKINO: u16 = 156;
        const ACHINSK: u16 = 157;
        const YELETS: u16 = 158;
        const SERGIYEV_POSAD: u16 = 159;
        const ARZAMAS: u16 = 160;
        const DOLGOPRUDNY: u16 = 161;
        const ELISTA: u16 = 162;
        const BERDSK: u16 = 163;
        const NOVOKUYBYSHEVSK: u16 = 164;
        const NOGINSK: u16 = 165;
        const ZHELEZNOGORSK_KURSK: u16 = 166;
        const REUTOV: u16 = 167;
        const TOBOLSK: u16 = 169;
        const KHANTY_MANSIYSK: u16 = 170;
        const VOTKINSK: u16 = 171;
        const SARAPUL: u16 = 172;
        const MEZHDURECHENSK: u16 = 173;
        const UKHTA: u16 = 174;
        const SEROV: u16 = 175;
        const LENINSK_KUZNETSKY: u16 = 176;
        const GATCHINA: u16 = 177;
        const SAROV: u16 = 178;
        const SOLIKAMSK: u16 = 179;
        const VOSKRESENSK: u16 = 180;
        const MICHURINSK: u16 = 181;
        const GLAZOV: u16 = 182;
        const VELIKIYE_LUKI: u16 = 183;
        const MAGADAN: u16 = 184;
        const KISELYOVSK: u16 = 185;
        const KANSK: u16 = 186;
        const KAMENSK_SHAKHTINSKY: u16 = 187;
        const NOVOTROITSK: u16 = 188;
        const MIKHAYLOVSK: u16 = 189;
        const LOBNYA: u16 = 190;
        const GUBKIN: u16 = 191;
        const BUZULUK: u16 = 192;
        const BUGULMA: u16 = 193;
        const YEYSK: u16 = 194;
        const ZHELEZNOGORSK_KRASNOJARSK: u16 = 195;
        const KINESHMA: u16 = 196;
        const CHAYKOVSKY: u16 = 197;
        const KUZNETSK: u16 = 198;
        const UST_ILIMSK: u16 = 199;
        const YURGA: u16 = 200;
        const NOVOURALSK: u16 = 201;
        const AZOV: u16 = 202;
        const OZYORSK: u16 = 203;
        const KROPOTKIN: u16 = 204;
        const KLIN: u16 = 205;
        const VYBORG: u16 = 206;
        const BOR: u16 = 207;
        const USOLYE_SIBIRSKOYE: u16 = 208;
        const BALASHOV: u16 = 209;
        const SHADRINSK: u16 = 210;
        const MINERALNYE_VODY: u16 = 211;
        const ANAPA: u16 = 212;
        const TROITSK: u16 = 213;
        const DUBNA: u16 = 214;
        const GELENDZHIK: u16 = 215;
        const CHERNOGORSK: u16 = 216;
        const IVANTEYEVKA: u16 = 217;
        const BIROBIDZHAN: u16 = 218;
        const YELABUGA: u16 = 219;
        const YEGORYEVSK: u16 = 220;
        const NOVOALTAYSK: u16 = 221;
        const KIROVO_CHEPETSK: u16 = 222;
        const CHAPAYEVSK: u16 = 223;
        const BELOVO: u16 = 214;
        const ANZHERO_SUDZHENSK: u16 = 215;
        const CHEKHOV: u16 = 226;
        const VSEVOLOZHSK: u16 = 227;
        const VERKHNYAYA_PYSHMA: u16 = 228;
        const GEORGIYEVSK: u16 = 229;
        const TUYMAZY: u16 = 230;
        const MINUSINSK: u16 = 231;
        const SOSNOVY_BOR: u16 = 232;
        const KSTOVO: u16 = 233;
        const DMITROV: u16 = 234;
        const BELOGORSK: u16 = 235;
        const STUPINO: u16 = 236;
        const GUKOVO: u16 = 237;
        const KUNGUR: u16 = 238;
        const SLAVYANSK_NA_KUBANI: u16 = 239;
        const BELORETSK: u16 = 240;
        const PAVLOVSKY_POSAD: u16 = 241;
        const ISHIMBAY: u16 = 242;
        const ISHIM: u16 = 243;
        const VIDNOYE: u16 = 244;
        const ZARECHNY: u16 = 245;
        const KOGALYM: u16 = 246;
        const ASBEST: u16 = 247;
        const BUYNAKSK: u16 = 248;
        const VOLSK: u16 = 249;
        const DONSKOY: u16 = 250;
        const GORNO_ALTAYSK: u16 = 251;
        const LENINOGORSK: u16 = 252;
        const ROSSOSH: u16 = 253;
        const TUAPSE: u16 = 254;
        const KLINTSY: u16 = 255;
        const BUDYONNOVSK: u16 = 256;
        const BORISOGLEBSK: u16 = 257;
        const REVDA: u16 = 258;
        const LYSVA: u16 = 259;
        const ZELENOGORSK: u16 = 260;
        const POLEVSKOY: u16 = 261;
        const NARO_FOMINSK: u16 = 262;
        const KOTLAS: u16 = 263;
        const SIBAY: u16 = 264;
        const LABINSK: u16 = 265;
        const KUMERTAU: u16 = 266;
        const CHISTOPOL: u16 = 267;
        const FRYAZINO: u16 = 268;
        const RZHEV: u16 = 269;
        const LESOSIBIRSK: u16 = 270;
        const ALEXANDROV: u16 = 271;
        const BELEBEY: u16 = 272;
        const TIKHORETSK: u16 = 273;
        const SHUYA: u16 = 274;
        const URUS_MARTAN: u16 = 275;
        const MELEUZ: u16 = 276;
        const MIKHAYLOVKA: u16 = 277;
        const ALEKSIN: u16 = 278;
        const SALSK: u16 = 279;
        const PAVLOVO: u16 = 280;
        const IZBERBASH: u16 = 281;
        const VORKUTA: u16 = 282;
        const SHCHYOKINO: u16 = 283;
        const TIKHVIN: u16 = 284;
        const PROKHLADNY: u16 = 285;
        const NYAGAN: u16 = 286;
        const LYTKARINO: u16 = 287;
        const KRASNOTURYINSK: u16 = 288;
        const KRYMSK: u16 = 289;
        const NERYUNGRI: u16 = 290;
        const BERYOZOVSKY: u16 = 291;
        const ISKITIM: u16 = 292;
        const APATITY: u16 = 293;
        const GUS_KHRUSTALNY: u16 = 294;
        const DZERZHINSKY: u16 = 295;
        const VOLZHSK: u16 = 296;
        const ZHIGULYOVSK: u16 = 297;
        const LISKI: u16 = 298;
        const SVOBODNY: u16 = 299;
        const KRASNOKAMSK: u16 = 300;
        const VYKSA: u16 = 301;
        const VYAZMA: u16 = 302;
        const SHALI: u16 = 303;
        const KRASNOKAMENSK: u16 = 304;
        const ARSENYEV: u16 = 305;
        const SOLNECHNOGORSK: u16 = 306;
        const TIMASHYOVSK: u16 = 307;
        const BELORECHENSK: u16 = 308;
        const KIRISHI: u16 = 309;
        const UZLOVAYA: u16 = 310;
        const GUDERMES: u16 = 311;
        const SERTOLOVO: u16 = 312;
        const CHEREMKHOVO: u16 = 313;
        const SEVEROMORSK: u16 = 314;
        const BOROVICHI: u16 = 315;
        const ROSLAVL: u16 = 316;
        const SNEZHINSK: u16 = 317;
        const NAZAROVO: u16 = 318;

        let city = BOROVICHI;
        if city == MOSCOW {
            print!("{:?}", MOSCOW);
        } else if city == MOSCOW {
            print!("{:?}", MOSCOW);
        } else if city == SAINT_PETERSBURG {
            print!("{:?}", SAINT_PETERSBURG);
        } else if city == NOVOSIBIRSK {
            print!("{:?}", NOVOSIBIRSK);
        } else if city == YEKATERINBURG {
            print!("{:?}", YEKATERINBURG);
        } else if city == NIZHNY_NOVGOROD {
            print!("{:?}", NIZHNY_NOVGOROD);
        } else if city == KAZAN {
            print!("{:?}", KAZAN);
        } else if city == CHELYABINSK {
            print!("{:?}", CHELYABINSK);
        } else if city == OMSK {
            print!("{:?}", OMSK);
        } else if city == SAMARA {
            print!("{:?}", SAMARA);
        } else if city == ROSTOV_ON_DON {
            print!("{:?}", ROSTOV_ON_DON);
        } else if city == UFA {
            print!("{:?}", UFA);
        } else if city == KRASNOYARSK {
            print!("{:?}", KRASNOYARSK);
        } else if city == PERM {
            print!("{:?}", PERM);
        } else if city == VORONEZH {
            print!("{:?}", VORONEZH);
        } else if city == VOLGOGRAD {
            print!("{:?}", VOLGOGRAD);
        } else if city == KRASNODAR {
            print!("{:?}", KRASNODAR);
        } else if city == SARATOV {
            print!("{:?}", SARATOV);
        } else if city == TYUMEN {
            print!("{:?}", TYUMEN);
        } else if city == TOLYATTI {
            print!("{:?}", TOLYATTI);
        } else if city == IZHEVSK {
            print!("{:?}", IZHEVSK);
        } else if city == BARNAUL {
            print!("{:?}", BARNAUL);
        } else if city == ULYANOVSK {
            print!("{:?}", ULYANOVSK);
        } else if city == IRKUTSK {
            print!("{:?}", IRKUTSK);
        } else if city == KHABAROVSK {
            print!("{:?}", KHABAROVSK);
        } else if city == YAROSLAVL {
            print!("{:?}", YAROSLAVL);
        } else if city == VLADIVOSTOK {
            print!("{:?}", VLADIVOSTOK);
        } else if city == MAKHACHKALA {
            print!("{:?}", MAKHACHKALA);
        } else if city == TOMSK {
            print!("{:?}", TOMSK);
        } else if city == ORENBURG {
            print!("{:?}", ORENBURG);
        } else if city == KEMEROVO {
            print!("{:?}", KEMEROVO);
        } else if city == NOVOKUZNETSK {
            print!("{:?}", NOVOKUZNETSK);
        } else if city == RYAZAN {
            print!("{:?}", RYAZAN);
        } else if city == ASTRAKHAN {
            print!("{:?}", ASTRAKHAN);
        } else if city == NABEREZHNYE_CHELNY {
            print!("{:?}", NABEREZHNYE_CHELNY);
        } else if city == PENZA {
            print!("{:?}", PENZA);
        } else if city == LIPETSK {
            print!("{:?}", LIPETSK);
        } else if city == KIROV {
            print!("{:?}", KIROV);
        } else if city == CHEBOKSARY {
            print!("{:?}", CHEBOKSARY);
        } else if city == TULA {
            print!("{:?}", TULA);
        } else if city == KALININGRAD {
            print!("{:?}", KALININGRAD);
        } else if city == BALASHIKHA {
            print!("{:?}", BALASHIKHA);
        } else if city == KURSK {
            print!("{:?}", KURSK);
        } else if city == STAVROPOL {
            print!("{:?}", STAVROPOL);
        } else if city == ULAN_UDE {
            print!("{:?}", ULAN_UDE);
        } else if city == TVER {
            print!("{:?}", TVER);
        } else if city == MAGNITOGORSK {
            print!("{:?}", MAGNITOGORSK);
        } else if city == SOCHI {
            print!("{:?}", SOCHI);
        } else if city == IVANOVO {
            print!("{:?}", IVANOVO);
        } else if city == BRYANSK {
            print!("{:?}", BRYANSK);
        } else if city == BELGOROD {
            print!("{:?}", BELGOROD);
        } else if city == SURGUT {
            print!("{:?}", SURGUT);
        } else if city == VLADIMIR {
            print!("{:?}", VLADIMIR);
        } else if city == NIZHNY_TAGIL {
            print!("{:?}", NIZHNY_TAGIL);
        } else if city == ARKHANGELSK {
            print!("{:?}", ARKHANGELSK);
        } else if city == CHITA {
            print!("{:?}", CHITA);
        } else if city == KALUGA {
            print!("{:?}", KALUGA);
        } else if city == SMOLENSK {
            print!("{:?}", SMOLENSK);
        } else if city == VOLZHSKY {
            print!("{:?}", VOLZHSKY);
        } else if city == KURGAN {
            print!("{:?}", KURGAN);
        } else if city == CHEREPOVETS {
            print!("{:?}", CHEREPOVETS);
        } else if city == ORYOL {
            print!("{:?}", ORYOL);
        } else if city == SARANSK {
            print!("{:?}", SARANSK);
        } else if city == VOLOGDA {
            print!("{:?}", VOLOGDA);
        } else if city == YAKUTSK {
            print!("{:?}", YAKUTSK);
        } else if city == VLADIKAVKAZ {
            print!("{:?}", VLADIKAVKAZ);
        } else if city == PODOLSK {
            print!("{:?}", PODOLSK);
        } else if city == MURMANSK {
            print!("{:?}", MURMANSK);
        } else if city == GROZNY {
            print!("{:?}", GROZNY);
        } else if city == TAMBOV {
            print!("{:?}", TAMBOV);
        } else if city == STERLITAMAK {
            print!("{:?}", STERLITAMAK);
        } else if city == PETROZAVODSK {
            print!("{:?}", PETROZAVODSK);
        } else if city == KOSTROMA {
            print!("{:?}", KOSTROMA);
        } else if city == NIZHNEVARTOVSK {
            print!("{:?}", NIZHNEVARTOVSK);
        } else if city == NOVOROSSIYSK {
            print!("{:?}", NOVOROSSIYSK);
        } else if city == YOSHKAR_OLA {
            print!("{:?}", YOSHKAR_OLA);
        } else if city == TAGANROG {
            print!("{:?}", TAGANROG);
        } else if city == KOMSOMOLSK_ON_AMUR {
            print!("{:?}", KOMSOMOLSK_ON_AMUR);
        } else if city == KHIMKI {
            print!("{:?}", KHIMKI);
        } else if city == SYKTYVKAR {
            print!("{:?}", SYKTYVKAR);
        } else if city == NALCHIK {
            print!("{:?}", NALCHIK);
        } else if city == NIZHNEKAMSK {
            print!("{:?}", NIZHNEKAMSK);
        } else if city == SHAKHTY {
            print!("{:?}", SHAKHTY);
        } else if city == DZERZHINSK {
            print!("{:?}", DZERZHINSK);
        } else if city == BRATSK {
            print!("{:?}", BRATSK);
        } else if city == ORSK {
            print!("{:?}", ORSK);
        } else if city == ANGARSK {
            print!("{:?}", ANGARSK);
        } else if city == ENGELS {
            print!("{:?}", ENGELS);
        } else if city == BLAGOVESHCHENSK {
            print!("{:?}", BLAGOVESHCHENSK);
        } else if city == STARY_OSKOL {
            print!("{:?}", STARY_OSKOL);
        } else if city == VELIKY_NOVGOROD {
            print!("{:?}", VELIKY_NOVGOROD);
        } else if city == KOROLYOV {
            print!("{:?}", KOROLYOV);
        } else if city == PSKOV {
            print!("{:?}", PSKOV);
        } else if city == MYTISHCHI {
            print!("{:?}", MYTISHCHI);
        } else if city == BIYSK {
            print!("{:?}", BIYSK);
        } else if city == LYUBERTSY {
            print!("{:?}", LYUBERTSY);
        } else if city == PROKOPYEVSK {
            print!("{:?}", PROKOPYEVSK);
        } else if city == YUZHNO_SAKHALINSK {
            print!("{:?}", YUZHNO_SAKHALINSK);
        } else if city == BALAKOVO {
            print!("{:?}", BALAKOVO);
        } else if city == ARMAVIR {
            print!("{:?}", ARMAVIR);
        } else if city == RYBINSK {
            print!("{:?}", RYBINSK);
        } else if city == SEVERODVINSK {
            print!("{:?}", SEVERODVINSK);
        } else if city == ABAKAN {
            print!("{:?}", ABAKAN);
        } else if city == PETROPAVLOVSK_KAMCHATSKY {
            print!("{:?}", PETROPAVLOVSK_KAMCHATSKY);
        } else if city == NORILSK {
            print!("{:?}", NORILSK);
        } else if city == SYZRAN {
            print!("{:?}", SYZRAN);
        } else if city == VOLGODONSK {
            print!("{:?}", VOLGODONSK);
        } else if city == USSURIYSK {
            print!("{:?}", USSURIYSK);
        } else if city == KAMENSK_URALSKY {
            print!("{:?}", KAMENSK_URALSKY);
        } else if city == NOVOCHERKASSK {
            print!("{:?}", NOVOCHERKASSK);
        } else if city == ZLATOUST {
            print!("{:?}", ZLATOUST);
        } else if city == ELEKTROSTAL {
            print!("{:?}", ELEKTROSTAL);
        } else if city == ALMETYEVSK {
            print!("{:?}", ALMETYEVSK);
        } else if city == KRASNOGORSK {
            print!("{:?}", KRASNOGORSK);
        } else if city == SALAVAT {
            print!("{:?}", SALAVAT);
        } else if city == MIASS {
            print!("{:?}", MIASS);
        } else if city == NAKHODKA {
            print!("{:?}", NAKHODKA);
        } else if city == KOPEYSK {
            print!("{:?}", KOPEYSK);
        } else if city == PYATIGORSK {
            print!("{:?}", PYATIGORSK);
        } else if city == RUBTSOVSK {
            print!("{:?}", RUBTSOVSK);
        } else if city == BEREZNIKI {
            print!("{:?}", BEREZNIKI);
        } else if city == KOLOMNA {
            print!("{:?}", KOLOMNA);
        } else if city == MAYKOP {
            print!("{:?}", MAYKOP);
        } else if city == ODINTSOVO {
            print!("{:?}", ODINTSOVO);
        } else if city == KHASAVYURT {
            print!("{:?}", KHASAVYURT);
        } else if city == KOVROV {
            print!("{:?}", KOVROV);
        } else if city == KISLOVODSK {
            print!("{:?}", KISLOVODSK);
        } else if city == NEFTEKAMSK {
            print!("{:?}", NEFTEKAMSK);
        } else if city == NEFTEYUGANSK {
            print!("{:?}", NEFTEYUGANSK);
        } else if city == NOVOCHEBOKSARSK {
            print!("{:?}", NOVOCHEBOKSARSK);
        } else if city == SERPUKHOV {
            print!("{:?}", SERPUKHOV);
        } else if city == SHCHYOLKOVO {
            print!("{:?}", SHCHYOLKOVO);
        } else if city == NOVOMOSKOVSK {
            print!("{:?}", NOVOMOSKOVSK);
        } else if city == BATAYSK {
            print!("{:?}", BATAYSK);
        } else if city == PERVOURALSK {
            print!("{:?}", PERVOURALSK);
        } else if city == DOMODEDOVO {
            print!("{:?}", DOMODEDOVO);
        } else if city == DERBENT {
            print!("{:?}", DERBENT);
        } else if city == CHERKESSK {
            print!("{:?}", CHERKESSK);
        } else if city == OREKHOVO_ZUYEVO {
            print!("{:?}", OREKHOVO_ZUYEVO);
        } else if city == NEVINNOMYSSK {
            print!("{:?}", NEVINNOMYSSK);
        } else if city == DIMITROVGRAD {
            print!("{:?}", DIMITROVGRAD);
        } else if city == NAZRAN {
            print!("{:?}", NAZRAN);
        } else if city == KYZYL {
            print!("{:?}", KYZYL);
        } else if city == OKTYABRSKY {
            print!("{:?}", OKTYABRSKY);
        } else if city == OBNINSK {
            print!("{:?}", OBNINSK);
        } else if city == KASPIYSK {
            print!("{:?}", KASPIYSK);
        } else if city == NOVY_URENGOY {
            print!("{:?}", NOVY_URENGOY);
        } else if city == RAMENSKOYE {
            print!("{:?}", RAMENSKOYE);
        } else if city == KAMYSHIN {
            print!("{:?}", KAMYSHIN);
        } else if city == MUROM {
            print!("{:?}", MUROM);
        } else if city == ZHUKOVSKY {
            print!("{:?}", ZHUKOVSKY);
        } else if city == NOVOSHAKHTINSK {
            print!("{:?}", NOVOSHAKHTINSK);
        } else if city == SEVERSK {
            print!("{:?}", SEVERSK);
        } else if city == YESSENTUKI {
            print!("{:?}", YESSENTUKI);
        } else if city == NOYABRSK {
            print!("{:?}", NOYABRSK);
        } else if city == ARTYOM {
            print!("{:?}", ARTYOM);
        } else if city == PUSHKINO {
            print!("{:?}", PUSHKINO);
        } else if city == ACHINSK {
            print!("{:?}", ACHINSK);
        } else if city == YELETS {
            print!("{:?}", YELETS);
        } else if city == SERGIYEV_POSAD {
            print!("{:?}", SERGIYEV_POSAD);
        } else if city == ARZAMAS {
            print!("{:?}", ARZAMAS);
        } else if city == DOLGOPRUDNY {
            print!("{:?}", DOLGOPRUDNY);
        } else if city == ELISTA {
            print!("{:?}", ELISTA);
        } else if city == BERDSK {
            print!("{:?}", BERDSK);
        } else if city == NOVOKUYBYSHEVSK {
            print!("{:?}", NOVOKUYBYSHEVSK);
        } else if city == NOGINSK {
            print!("{:?}", NOGINSK);
        } else if city == REUTOV {
            print!("{:?}", REUTOV);
        } else if city == ZHELEZNOGORSK_KURSK {
            print!("{:?}", ZHELEZNOGORSK_KURSK);
        } else if city == TOBOLSK {
            print!("{:?}", TOBOLSK);
        } else if city == KHANTY_MANSIYSK {
            print!("{:?}", KHANTY_MANSIYSK);
        } else if city == VOTKINSK {
            print!("{:?}", VOTKINSK);
        } else if city == SARAPUL {
            print!("{:?}", SARAPUL);
        } else if city == MEZHDURECHENSK {
            print!("{:?}", MEZHDURECHENSK);
        } else if city == UKHTA {
            print!("{:?}", UKHTA);
        } else if city == SEROV {
            print!("{:?}", SEROV);
        } else if city == LENINSK_KUZNETSKY {
            print!("{:?}", LENINSK_KUZNETSKY);
        } else if city == GATCHINA {
            print!("{:?}", GATCHINA);
        } else if city == SAROV {
            print!("{:?}", SAROV);
        } else if city == SOLIKAMSK {
            print!("{:?}", SOLIKAMSK);
        } else if city == VOSKRESENSK {
            print!("{:?}", VOSKRESENSK);
        } else if city == MICHURINSK {
            print!("{:?}", MICHURINSK);
        } else if city == GLAZOV {
            print!("{:?}", GLAZOV);
        } else if city == VELIKIYE_LUKI {
            print!("{:?}", VELIKIYE_LUKI);
        } else if city == MAGADAN {
            print!("{:?}", MAGADAN);
        } else if city == KISELYOVSK {
            print!("{:?}", KISELYOVSK);
        } else if city == KANSK {
            print!("{:?}", KANSK);
        } else if city == KAMENSK_SHAKHTINSKY {
            print!("{:?}", KAMENSK_SHAKHTINSKY);
        } else if city == NOVOTROITSK {
            print!("{:?}", NOVOTROITSK);
        } else if city == MIKHAYLOVSK {
            print!("{:?}", MIKHAYLOVSK);
        } else if city == LOBNYA {
            print!("{:?}", LOBNYA);
        } else if city == GUBKIN {
            print!("{:?}", GUBKIN);
        } else if city == BUZULUK {
            print!("{:?}", BUZULUK);
        } else if city == BUGULMA {
            print!("{:?}", BUGULMA);
        } else if city == YEYSK {
            print!("{:?}", YEYSK);
        } else if city == ZHELEZNOGORSK_KRASNOJARSK {
            print!("{:?}", ZHELEZNOGORSK_KRASNOJARSK);
        } else if city == KINESHMA {
            print!("{:?}", KINESHMA);
        } else if city == CHAYKOVSKY {
            print!("{:?}", CHAYKOVSKY);
        } else if city == KUZNETSK {
            print!("{:?}", KUZNETSK);
        } else if city == UST_ILIMSK {
            print!("{:?}", UST_ILIMSK);
        } else if city == YURGA {
            print!("{:?}", YURGA);
        } else if city == NOVOURALSK {
            print!("{:?}", NOVOURALSK);
        } else if city == AZOV {
            print!("{:?}", AZOV);
        } else if city == OZYORSK {
            print!("{:?}", OZYORSK);
        } else if city == KROPOTKIN {
            print!("{:?}", KROPOTKIN);
        } else if city == KLIN {
            print!("{:?}", KLIN);
        } else if city == VYBORG {
            print!("{:?}", VYBORG);
        } else if city == BOR {
            print!("{:?}", BOR);
        } else if city == USOLYE_SIBIRSKOYE {
            print!("{:?}", USOLYE_SIBIRSKOYE);
        } else if city == BALASHOV {
            print!("{:?}", BALASHOV);
        } else if city == SHADRINSK {
            print!("{:?}", SHADRINSK);
        } else if city == MINERALNYE_VODY {
            print!("{:?}", MINERALNYE_VODY);
        } else if city == ANAPA {
            print!("{:?}", ANAPA);
        } else if city == TROITSK {
            print!("{:?}", TROITSK);
        } else if city == DUBNA {
            print!("{:?}", DUBNA);
        } else if city == GELENDZHIK {
            print!("{:?}", GELENDZHIK);
        } else if city == CHERNOGORSK {
            print!("{:?}", CHERNOGORSK);
        } else if city == IVANTEYEVKA {
            print!("{:?}", IVANTEYEVKA);
        } else if city == BIROBIDZHAN {
            print!("{:?}", BIROBIDZHAN);
        } else if city == YELABUGA {
            print!("{:?}", YELABUGA);
        } else if city == YEGORYEVSK {
            print!("{:?}", YEGORYEVSK);
        } else if city == NOVOALTAYSK {
            print!("{:?}", NOVOALTAYSK);
        } else if city == KIROVO_CHEPETSK {
            print!("{:?}", KIROVO_CHEPETSK);
        } else if city == CHAPAYEVSK {
            print!("{:?}", CHAPAYEVSK);
        } else if city == BELOVO {
            print!("{:?}", BELOVO);
        } else if city == ANZHERO_SUDZHENSK {
            print!("{:?}", ANZHERO_SUDZHENSK);
        } else if city == CHEKHOV {
            print!("{:?}", CHEKHOV);
        } else if city == VSEVOLOZHSK {
            print!("{:?}", VSEVOLOZHSK);
        } else if city == VERKHNYAYA_PYSHMA {
            print!("{:?}", VERKHNYAYA_PYSHMA);
        } else if city == GEORGIYEVSK {
            print!("{:?}", GEORGIYEVSK);
        } else if city == TUYMAZY {
            print!("{:?}", TUYMAZY);
        } else if city == MINUSINSK {
            print!("{:?}", MINUSINSK);
        } else if city == SOSNOVY_BOR {
            print!("{:?}", SOSNOVY_BOR);
        } else if city == KSTOVO {
            print!("{:?}", KSTOVO);
        } else if city == DMITROV {
            print!("{:?}", DMITROV);
        } else if city == BELOGORSK {
            print!("{:?}", BELOGORSK);
        } else if city == STUPINO {
            print!("{:?}", STUPINO);
        } else if city == GUKOVO {
            print!("{:?}", GUKOVO);
        } else if city == KUNGUR {
            print!("{:?}", KUNGUR);
        } else if city == SLAVYANSK_NA_KUBANI {
            print!("{:?}", SLAVYANSK_NA_KUBANI);
        } else if city == BELORETSK {
            print!("{:?}", BELORETSK);
        } else if city == PAVLOVSKY_POSAD {
            print!("{:?}", PAVLOVSKY_POSAD);
        } else if city == ISHIMBAY {
            print!("{:?}", ISHIMBAY);
        } else if city == ISHIM {
            print!("{:?}", ISHIM);
        } else if city == VIDNOYE {
            print!("{:?}", VIDNOYE);
        } else if city == ZARECHNY {
            print!("{:?}", ZARECHNY);
        } else if city == KOGALYM {
            print!("{:?}", KOGALYM);
        } else if city == ASBEST {
            print!("{:?}", ASBEST);
        } else if city == BUYNAKSK {
            print!("{:?}", BUYNAKSK);
        } else if city == VOLSK {
            print!("{:?}", VOLSK);
        } else if city == DONSKOY {
            print!("{:?}", DONSKOY);
        } else if city == GORNO_ALTAYSK {
            print!("{:?}", GORNO_ALTAYSK);
        } else if city == LENINOGORSK {
            print!("{:?}", LENINOGORSK);
        } else if city == ROSSOSH {
            print!("{:?}", ROSSOSH);
        } else if city == TUAPSE {
            print!("{:?}", TUAPSE);
        } else if city == KLINTSY {
            print!("{:?}", KLINTSY);
        } else if city == BUDYONNOVSK {
            print!("{:?}", BUDYONNOVSK);
        } else if city == BORISOGLEBSK {
            print!("{:?}", BORISOGLEBSK);
        } else if city == REVDA {
            print!("{:?}", REVDA);
        } else if city == LYSVA {
            print!("{:?}", LYSVA);
        } else if city == ZELENOGORSK {
            print!("{:?}", ZELENOGORSK);
        } else if city == POLEVSKOY {
            print!("{:?}", POLEVSKOY);
        } else if city == NARO_FOMINSK {
            print!("{:?}", NARO_FOMINSK);
        } else if city == KOTLAS {
            print!("{:?}", KOTLAS);
        } else if city == SIBAY {
            print!("{:?}", SIBAY);
        } else if city == LABINSK {
            print!("{:?}", LABINSK);
        } else if city == KUMERTAU {
            print!("{:?}", KUMERTAU);
        } else if city == CHISTOPOL {
            print!("{:?}", CHISTOPOL);
        } else if city == FRYAZINO {
            print!("{:?}", FRYAZINO);
        } else if city == RZHEV {
            print!("{:?}", RZHEV);
        } else if city == LESOSIBIRSK {
            print!("{:?}", LESOSIBIRSK);
        } else if city == ALEXANDROV {
            print!("{:?}", ALEXANDROV);
        } else if city == BELEBEY {
            print!("{:?}", BELEBEY);
        } else if city == TIKHORETSK {
            print!("{:?}", TIKHORETSK);
        } else if city == SHUYA {
            print!("{:?}", SHUYA);
        } else if city == URUS_MARTAN {
            print!("{:?}", URUS_MARTAN);
        } else if city == MELEUZ {
            print!("{:?}", MELEUZ);
        } else if city == MIKHAYLOVKA {
            print!("{:?}", MIKHAYLOVKA);
        } else if city == ALEKSIN {
            print!("{:?}", ALEKSIN);
        } else if city == SALSK {
            print!("{:?}", SALSK);
        } else if city == PAVLOVO {
            print!("{:?}", PAVLOVO);
        } else if city == IZBERBASH {
            print!("{:?}", IZBERBASH);
        } else if city == VORKUTA {
            print!("{:?}", VORKUTA);
        } else if city == SHCHYOKINO {
            print!("{:?}", SHCHYOKINO);
        } else if city == TIKHVIN {
            print!("{:?}", TIKHVIN);
        } else if city == PROKHLADNY {
            print!("{:?}", PROKHLADNY);
        } else if city == NYAGAN {
            print!("{:?}", NYAGAN);
        } else if city == LYTKARINO {
            print!("{:?}", LYTKARINO);
        } else if city == KRASNOTURYINSK {
            print!("{:?}", KRASNOTURYINSK);
        } else if city == KRYMSK {
            print!("{:?}", KRYMSK);
        } else if city == NERYUNGRI {
            print!("{:?}", NERYUNGRI);
        } else if city == BERYOZOVSKY {
            print!("{:?}", BERYOZOVSKY);
        } else if city == ISKITIM {
            print!("{:?}", ISKITIM);
        } else if city == APATITY {
            print!("{:?}", APATITY);
        } else if city == GUS_KHRUSTALNY {
            print!("{:?}", GUS_KHRUSTALNY);
        } else if city == DZERZHINSKY {
            print!("{:?}", DZERZHINSKY);
        } else if city == VOLZHSK {
            print!("{:?}", VOLZHSK);
        } else if city == ZHIGULYOVSK {
            print!("{:?}", ZHIGULYOVSK);
        } else if city == LISKI {
            print!("{:?}", LISKI);
        } else if city == SVOBODNY {
            print!("{:?}", SVOBODNY);
        } else if city == KRASNOKAMSK {
            print!("{:?}", KRASNOKAMSK);
        } else if city == VYKSA {
            print!("{:?}", VYKSA);
        } else if city == VYAZMA {
            print!("{:?}", VYAZMA);
        } else if city == SHALI {
            print!("{:?}", SHALI);
        } else if city == KRASNOKAMENSK {
            print!("{:?}", KRASNOKAMENSK);
        } else if city == ARSENYEV {
            print!("{:?}", ARSENYEV);
        } else if city == SOLNECHNOGORSK {
            print!("{:?}", SOLNECHNOGORSK);
        } else if city == TIMASHYOVSK {
            print!("{:?}", TIMASHYOVSK);
        } else if city == BELORECHENSK {
            print!("{:?}", BELORECHENSK);
        } else if city == KIRISHI {
            print!("{:?}", KIRISHI);
        } else if city == UZLOVAYA {
            print!("{:?}", UZLOVAYA);
        } else if city == GUDERMES {
            print!("{:?}", GUDERMES);
        } else if city == SERTOLOVO {
            print!("{:?}", SERTOLOVO);
        } else if city == CHEREMKHOVO {
            print!("{:?}", CHEREMKHOVO);
        } else if city == SEVEROMORSK {
            print!("{:?}", SEVEROMORSK);
        } else if city == BOROVICHI {
            print!("{:?}", BOROVICHI);
        } else if city == ROSLAVL {
            print!("{:?}", ROSLAVL);
        } else if city == SNEZHINSK {
            print!("{:?}", SNEZHINSK);
        } else if city == NAZAROVO {
            print!("{:?}", NAZAROVO);
        }
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=01b768543f978b4a727ebe0ce9bc3159&version=stable&mode=debug&edition=2015)

Конечно, сгруппирвоать города каким-либо образом - очевидное решение.
```rust
#[allow(dead_code)]
enum RussianCity {
    Moscow,
    SaintPetersburg,
    Novosibirsk,
    Yekaterinburg,
    NizhnyNovgorod,
    Kazan,
    Chelyabinsk,
    Omsk,
    Samara,
    RostovonDon,
    Ufa,
    Krasnoyarsk,
    Perm,
    Voronezh,
    Volgograd,
    Krasnodar,
    Saratov,
    Tyumen,
    Tolyatti,
    Izhevsk,
    Barnaul,
    Ulyanovsk,
    Irkutsk,
    Khabarovsk,
    Yaroslavl,
    Vladivostok,
    Makhachkala,
    Tomsk,
    Orenburg,
    Kemerovo,
    Novokuznetsk,
    Ryazan,
    Astrakhan,
    NaberezhnyeChelny,
    Penza,
    Lipetsk,
    Kirov,
    Cheboksary,
    Tula,
    Kaliningrad,
    Balashikha,
    Kursk,
    Stavropol,
    UlanUde,
    Tver,
    Magnitogorsk,
    Sochi,
    Ivanovo,
    Bryansk,
    Belgorod,
    Surgut,
    Vladimir,
    NizhnyTagil,
    Arkhangelsk,
    Chita,
    Kaluga,
    Smolensk,
    Volzhsky,
    Kurgan,
    Cherepovets,
    Oryol,
    Saransk,
    Vologda,
    Yakutsk,
    Vladikavkaz,
    Podolsk,
    Murmansk,
    Grozny,
    Tambov,
    Sterlitamak,
    Petrozavodsk,
    Kostroma,
    Nizhnevartovsk,
    Novorossiysk,
    YoshkarOla,
    Taganrog,
    KomsomolskonAmur,
    Khimki,
    Syktyvkar,
    Nalchik,
    Nizhnekamsk,
    Shakhty,
    Dzerzhinsk,
    Bratsk,
    Orsk,
    Angarsk,
    Engels,
    Blagoveshchensk,
    StaryOskol,
    VelikyNovgorod,
    Korolyov,
    Pskov,
    Mytishchi,
    Biysk,
    Lyubertsy,
    Prokopyevsk,
    YuzhnoSakhalinsk,
    Balakovo,
    Armavir,
    Rybinsk,
    Severodvinsk,
    Abakan,
    PetropavlovskKamchatsky,
    Norilsk,
    Syzran,
    Volgodonsk,
    Ussuriysk,
    KamenskUralsky,
    Novocherkassk,
    Zlatoust,
    Elektrostal,
    Almetyevsk,
    Krasnogorsk,
    Salavat,
    Miass,
    Nakhodka,
    Kopeysk,
    Pyatigorsk,
    Rubtsovsk,
    Berezniki,
    Kolomna,
    Maykop,
    Odintsovo,
    Khasavyurt,
    Kovrov,
    Kislovodsk,
    Neftekamsk,
    Nefteyugansk,
    Novocheboksarsk,
    Serpukhov,
    Shchyolkovo,
    Novomoskovsk,
    Bataysk,
    Pervouralsk,
    Domodedovo,
    Derbent,
    Cherkessk,
    OrekhovoZuyevo,
    Nevinnomyssk,
    Dimitrovgrad,
    Nazran,
    Kyzyl,
    Oktyabrsky,
    Obninsk,
    Kaspiysk,
    NovyUrengoy,
    Ramenskoye,
    Kamyshin,
    Murom,
    Zhukovsky,
    Novoshakhtinsk,
    Seversk,
    Yessentuki,
    Noyabrsk,
    Artyom,
    Pushkino,
    Achinsk,
    Yelets,
    SergiyevPosad,
    Arzamas,
    Dolgoprudny,
    Elista,
    Berdsk,
    Novokuybyshevsk,
    Noginsk,
    Reutov,
    ZHELEZNOGORSKKURSK,
    Tobolsk,
    KhantyMansiysk,
    Votkinsk,
    Sarapul,
    Mezhdurechensk,
    Ukhta,
    Serov,
    LeninskKuznetsky,
    Gatchina,
    Sarov,
    Solikamsk,
    Voskresensk,
    Michurinsk,
    Glazov,
    VelikiyeLuki,
    Magadan,
    Kiselyovsk,
    Kansk,
    KamenskShakhtinsky,
    Novotroitsk,
    Mikhaylovsk,
    Lobnya,
    Gubkin,
    Buzuluk,
    Bugulma,
    Yeysk,
    ZHELEZNOGORSKKRASNOJARSK,
    Kineshma,
    Chaykovsky,
    Kuznetsk,
    UstIlimsk,
    Yurga,
    Novouralsk,
    Azov,
    Ozyorsk,
    Kropotkin,
    Klin,
    Vyborg,
    Bor,
    UsolyeSibirskoye,
    Balashov,
    Shadrinsk,
    MineralnyeVody,
    Anapa,
    Troitsk,
    Dubna,
    Gelendzhik,
    Chernogorsk,
    Ivanteyevka,
    Birobidzhan,
    Yelabuga,
    Yegoryevsk,
    Novoaltaysk,
    KirovoChepetsk,
    Chapayevsk,
    Belovo,
    AnzheroSudzhensk,
    Chekhov,
    Vsevolozhsk,
    VerkhnyayaPyshma,
    Georgiyevsk,
    Tuymazy,
    Minusinsk,
    SosnovyBor,
    Kstovo,
    Dmitrov,
    Belogorsk,
    Stupino,
    Gukovo,
    Kungur,
    SlavyansknaKubani,
    Beloretsk,
    PavlovskyPosad,
    Ishimbay,
    Ishim,
    Vidnoye,
    Zarechny,
    Kogalym,
    Asbest,
    Buynaksk,
    Volsk,
    Donskoy,
    GornoAltaysk,
    Leninogorsk,
    Rossosh,
    Tuapse,
    Klintsy,
    Budyonnovsk,
    Borisoglebsk,
    Revda,
    Lysva,
    Zelenogorsk,
    Polevskoy,
    NaroFominsk,
    Kotlas,
    Sibay,
    Labinsk,
    Kumertau,
    Chistopol,
    Fryazino,
    Rzhev,
    Lesosibirsk,
    Alexandrov,
    Belebey,
    Tikhoretsk,
    Shuya,
    UrusMartan,
    Meleuz,
    Mikhaylovka,
    Aleksin,
    Salsk,
    Pavlovo,
    Izberbash,
    Vorkuta,
    Shchyokino,
    Tikhvin,
    Prokhladny,
    Nyagan,
    Lytkarino,
    Krasnoturyinsk,
    Krymsk,
    Neryungri,
    Beryozovsky,
    Iskitim,
    Apatity,
    GusKhrustalny,
    Dzerzhinsky,
    Volzhsk,
    Zhigulyovsk,
    Liski,
    Svobodny,
    Krasnokamsk,
    Vyksa,
    Vyazma,
    Shali,
    Krasnokamensk,
    Arsenyev,
    Solnechnogorsk,
    Timashyovsk,
    Belorechensk,
    Kirishi,
    Uzlovaya,
    Gudermes,
    Sertolovo,
    Cheremkhovo,
    Severomorsk,
    Borovichi,
    Roslavl,
    Snezhinsk,
    Nazarovo,
}
fn main() {
    let city = RussianCity::Roslavl;
    match city {
        RussianCity::Moscow => println!("Moscow"),
        RussianCity::SaintPetersburg => println!("SaintPetersburg"),
        RussianCity::Novosibirsk => println!("Novosibirsk"),
        RussianCity::Yekaterinburg => println!("Yekaterinburg"),
        RussianCity::NizhnyNovgorod => println!("NizhnyNovgorod"),
        RussianCity::Kazan => println!("Kazan"),
        RussianCity::Chelyabinsk => println!("Chelyabinsk"),
        RussianCity::Omsk => println!("Omsk"),
        RussianCity::Samara => println!("Samara"),
        RussianCity::RostovonDon => println!("RostovonDon"),
        RussianCity::Ufa => println!("Ufa"),
        RussianCity::Krasnoyarsk => println!("Krasnoyarsk"),
        RussianCity::Perm => println!("Perm"),
        RussianCity::Voronezh => println!("Voronezh"),
        RussianCity::Volgograd => println!("Volgograd"),
        RussianCity::Krasnodar => println!("Krasnodar"),
        RussianCity::Saratov => println!("Saratov"),
        RussianCity::Tyumen => println!("Tyumen"),
        RussianCity::Tolyatti => println!("Tolyatti"),
        RussianCity::Izhevsk => println!("Izhevsk"),
        RussianCity::Barnaul => println!("Barnaul"),
        RussianCity::Ulyanovsk => println!("Ulyanovsk"),
        RussianCity::Irkutsk => println!("Irkutsk"),
        RussianCity::Khabarovsk => println!("Khabarovsk"),
        RussianCity::Yaroslavl => println!("Yaroslavl"),
        RussianCity::Vladivostok => println!("Vladivostok"),
        RussianCity::Makhachkala => println!("Makhachkala"),
        RussianCity::Tomsk => println!("Tomsk"),
        RussianCity::Orenburg => println!("Orenburg"),
        RussianCity::Kemerovo => println!("Kemerovo"),
        RussianCity::Novokuznetsk => println!("Novokuznetsk"),
        RussianCity::Ryazan => println!("Ryazan"),
        RussianCity::Astrakhan => println!("Astrakhan"),
        RussianCity::NaberezhnyeChelny => println!("NaberezhnyeChelny"),
        RussianCity::Penza => println!("Penza"),
        RussianCity::Lipetsk => println!("Lipetsk"),
        RussianCity::Kirov => println!("Kirov"),
        RussianCity::Cheboksary => println!("Cheboksary"),
        RussianCity::Tula => println!("Tula"),
        RussianCity::Kaliningrad => println!("Kaliningrad"),
        RussianCity::Balashikha => println!("Balashikha"),
        RussianCity::Kursk => println!("Kursk"),
        RussianCity::Stavropol => println!("Stavropol"),
        RussianCity::UlanUde => println!("UlanUde"),
        RussianCity::Tver => println!("Tver"),
        RussianCity::Magnitogorsk => println!("Magnitogorsk"),
        RussianCity::Sochi => println!("Sochi"),
        RussianCity::Ivanovo => println!("Ivanovo"),
        RussianCity::Bryansk => println!("Bryansk"),
        RussianCity::Belgorod => println!("Belgorod"),
        RussianCity::Surgut => println!("Surgut"),
        RussianCity::Vladimir => println!("Vladimir"),
        RussianCity::NizhnyTagil => println!("NizhnyTagil"),
        RussianCity::Arkhangelsk => println!("Arkhangelsk"),
        RussianCity::Chita => println!("Chita"),
        RussianCity::Kaluga => println!("Kaluga"),
        RussianCity::Smolensk => println!("Smolensk"),
        RussianCity::Volzhsky => println!("Volzhsky"),
        RussianCity::Kurgan => println!("Kurgan"),
        RussianCity::Cherepovets => println!("Cherepovets"),
        RussianCity::Oryol => println!("Oryol"),
        RussianCity::Saransk => println!("Saransk"),
        RussianCity::Vologda => println!("Vologda"),
        RussianCity::Yakutsk => println!("Yakutsk"),
        RussianCity::Vladikavkaz => println!("Vladikavkaz"),
        RussianCity::Podolsk => println!("Podolsk"),
        RussianCity::Murmansk => println!("Murmansk"),
        RussianCity::Grozny => println!("Grozny"),
        RussianCity::Tambov => println!("Tambov"),
        RussianCity::Sterlitamak => println!("Sterlitamak"),
        RussianCity::Petrozavodsk => println!("Petrozavodsk"),
        RussianCity::Kostroma => println!("Kostroma"),
        RussianCity::Nizhnevartovsk => println!("Nizhnevartovsk"),
        RussianCity::Novorossiysk => println!("Novorossiysk"),
        RussianCity::YoshkarOla => println!("YoshkarOla"),
        RussianCity::Taganrog => println!("Taganrog"),
        RussianCity::KomsomolskonAmur => println!("KomsomolskonAmur"),
        RussianCity::Khimki => println!("Khimki"),
        RussianCity::Syktyvkar => println!("Syktyvkar"),
        RussianCity::Nalchik => println!("Nalchik"),
        RussianCity::Nizhnekamsk => println!("Nizhnekamsk"),
        RussianCity::Shakhty => println!("Shakhty"),
        RussianCity::Dzerzhinsk => println!("Dzerzhinsk"),
        RussianCity::Bratsk => println!("Bratsk"),
        RussianCity::Orsk => println!("Orsk"),
        RussianCity::Angarsk => println!("Angarsk"),
        RussianCity::Engels => println!("Engels"),
        RussianCity::Blagoveshchensk => println!("Blagoveshchensk"),
        RussianCity::StaryOskol => println!("StaryOskol"),
        RussianCity::VelikyNovgorod => println!("VelikyNovgorod"),
        RussianCity::Korolyov => println!("Korolyov"),
        RussianCity::Pskov => println!("Pskov"),
        RussianCity::Mytishchi => println!("Mytishchi"),
        RussianCity::Biysk => println!("Biysk"),
        RussianCity::Lyubertsy => println!("Lyubertsy"),
        RussianCity::Prokopyevsk => println!("Prokopyevsk"),
        RussianCity::YuzhnoSakhalinsk => println!("YuzhnoSakhalinsk"),
        RussianCity::Balakovo => println!("Balakovo"),
        RussianCity::Armavir => println!("Armavir"),
        RussianCity::Rybinsk => println!("Rybinsk"),
        RussianCity::Severodvinsk => println!("Severodvinsk"),
        RussianCity::Abakan => println!("Abakan"),
        RussianCity::PetropavlovskKamchatsky => println!("PetropavlovskKamchatsky"),
        RussianCity::Norilsk => println!("Norilsk"),
        RussianCity::Syzran => println!("Syzran"),
        RussianCity::Volgodonsk => println!("Volgodonsk"),
        RussianCity::Ussuriysk => println!("Ussuriysk"),
        RussianCity::KamenskUralsky => println!("KamenskUralsky"),
        RussianCity::Novocherkassk => println!("Novocherkassk"),
        RussianCity::Zlatoust => println!("Zlatoust"),
        RussianCity::Elektrostal => println!("Elektrostal"),
        RussianCity::Almetyevsk => println!("Almetyevsk"),
        RussianCity::Krasnogorsk => println!("Krasnogorsk"),
        RussianCity::Salavat => println!("Salavat"),
        RussianCity::Miass => println!("Miass"),
        RussianCity::Nakhodka => println!("Nakhodka"),
        RussianCity::Kopeysk => println!("Kopeysk"),
        RussianCity::Pyatigorsk => println!("Pyatigorsk"),
        RussianCity::Rubtsovsk => println!("Rubtsovsk"),
        RussianCity::Berezniki => println!("Berezniki"),
        RussianCity::Kolomna => println!("Kolomna"),
        RussianCity::Maykop => println!("Maykop"),
        RussianCity::Odintsovo => println!("Odintsovo"),
        RussianCity::Khasavyurt => println!("Khasavyurt"),
        RussianCity::Kovrov => println!("Kovrov"),
        RussianCity::Kislovodsk => println!("Kislovodsk"),
        RussianCity::Neftekamsk => println!("Neftekamsk"),
        RussianCity::Nefteyugansk => println!("Nefteyugansk"),
        RussianCity::Novocheboksarsk => println!("Novocheboksarsk"),
        RussianCity::Serpukhov => println!("Serpukhov"),
        RussianCity::Shchyolkovo => println!("Shchyolkovo"),
        RussianCity::Novomoskovsk => println!("Novomoskovsk"),
        RussianCity::Bataysk => println!("Bataysk"),
        RussianCity::Pervouralsk => println!("Pervouralsk"),
        RussianCity::Domodedovo => println!("Domodedovo"),
        RussianCity::Derbent => println!("Derbent"),
        RussianCity::Cherkessk => println!("Cherkessk"),
        RussianCity::OrekhovoZuyevo => println!("OrekhovoZuyevo"),
        RussianCity::Nevinnomyssk => println!("Nevinnomyssk"),
        RussianCity::Dimitrovgrad => println!("Dimitrovgrad"),
        RussianCity::Nazran => println!("Nazran"),
        RussianCity::Kyzyl => println!("Kyzyl"),
        RussianCity::Oktyabrsky => println!("Oktyabrsky"),
        RussianCity::Obninsk => println!("Obninsk"),
        RussianCity::Kaspiysk => println!("Kaspiysk"),
        RussianCity::NovyUrengoy => println!("NovyUrengoy"),
        RussianCity::Ramenskoye => println!("Ramenskoye"),
        RussianCity::Kamyshin => println!("Kamyshin"),
        RussianCity::Murom => println!("Murom"),
        RussianCity::Zhukovsky => println!("Zhukovsky"),
        RussianCity::Novoshakhtinsk => println!("Novoshakhtinsk"),
        RussianCity::Seversk => println!("Seversk"),
        RussianCity::Yessentuki => println!("Yessentuki"),
        RussianCity::Noyabrsk => println!("Noyabrsk"),
        RussianCity::Artyom => println!("Artyom"),
        RussianCity::Pushkino => println!("Pushkino"),
        RussianCity::Achinsk => println!("Achinsk"),
        RussianCity::Yelets => println!("Yelets"),
        RussianCity::SergiyevPosad => println!("SergiyevPosad"),
        RussianCity::Arzamas => println!("Arzamas"),
        RussianCity::Dolgoprudny => println!("Dolgoprudny"),
        RussianCity::Elista => println!("Elista"),
        RussianCity::Berdsk => println!("Berdsk"),
        RussianCity::Novokuybyshevsk => println!("Novokuybyshevsk"),
        RussianCity::Noginsk => println!("Noginsk"),
        RussianCity::Reutov => println!("Reutov"),
        RussianCity::ZHELEZNOGORSKKURSK => println!("ZHELEZNOGORSKKURSK"),
        RussianCity::Tobolsk => println!("Tobolsk"),
        RussianCity::KhantyMansiysk => println!("KhantyMansiysk"),
        RussianCity::Votkinsk => println!("Votkinsk"),
        RussianCity::Sarapul => println!("Sarapul"),
        RussianCity::Mezhdurechensk => println!("Mezhdurechensk"),
        RussianCity::Ukhta => println!("Ukhta"),
        RussianCity::Serov => println!("Serov"),
        RussianCity::LeninskKuznetsky => println!("LeninskKuznetsky"),
        RussianCity::Gatchina => println!("Gatchina"),
        RussianCity::Sarov => println!("Sarov"),
        RussianCity::Solikamsk => println!("Solikamsk"),
        RussianCity::Voskresensk => println!("Voskresensk"),
        RussianCity::Michurinsk => println!("Michurinsk"),
        RussianCity::Glazov => println!("Glazov"),
        RussianCity::VelikiyeLuki => println!("VelikiyeLuki"),
        RussianCity::Magadan => println!("Magadan"),
        RussianCity::Kiselyovsk => println!("Kiselyovsk"),
        RussianCity::Kansk => println!("Kansk"),
        RussianCity::KamenskShakhtinsky => println!("KamenskShakhtinsky"),
        RussianCity::Novotroitsk => println!("Novotroitsk"),
        RussianCity::Mikhaylovsk => println!("Mikhaylovsk"),
        RussianCity::Lobnya => println!("Lobnya"),
        RussianCity::Gubkin => println!("Gubkin"),
        RussianCity::Buzuluk => println!("Buzuluk"),
        RussianCity::Bugulma => println!("Bugulma"),
        RussianCity::Yeysk => println!("Yeysk"),
        RussianCity::ZHELEZNOGORSKKRASNOJARSK => println!("ZHELEZNOGORSKKRASNOJARSK"),
        RussianCity::Kineshma => println!("Kineshma"),
        RussianCity::Chaykovsky => println!("Chaykovsky"),
        RussianCity::Kuznetsk => println!("Kuznetsk"),
        RussianCity::UstIlimsk => println!("UstIlimsk"),
        RussianCity::Yurga => println!("Yurga"),
        RussianCity::Novouralsk => println!("Novouralsk"),
        RussianCity::Azov => println!("Azov"),
        RussianCity::Ozyorsk => println!("Ozyorsk"),
        RussianCity::Kropotkin => println!("Kropotkin"),
        RussianCity::Klin => println!("Klin"),
        RussianCity::Vyborg => println!("Vyborg"),
        RussianCity::Bor => println!("Bor"),
        RussianCity::UsolyeSibirskoye => println!("UsolyeSibirskoye"),
        RussianCity::Balashov => println!("Balashov"),
        RussianCity::Shadrinsk => println!("Shadrinsk"),
        RussianCity::MineralnyeVody => println!("MineralnyeVody"),
        RussianCity::Anapa => println!("Anapa"),
        RussianCity::Troitsk => println!("Troitsk"),
        RussianCity::Dubna => println!("Dubna"),
        RussianCity::Gelendzhik => println!("Gelendzhik"),
        RussianCity::Chernogorsk => println!("Chernogorsk"),
        RussianCity::Ivanteyevka => println!("Ivanteyevka"),
        RussianCity::Birobidzhan => println!("Birobidzhan"),
        RussianCity::Yelabuga => println!("Yelabuga"),
        RussianCity::Yegoryevsk => println!("Yegoryevsk"),
        RussianCity::Novoaltaysk => println!("Novoaltaysk"),
        RussianCity::KirovoChepetsk => println!("KirovoChepetsk"),
        RussianCity::Chapayevsk => println!("Chapayevsk"),
        RussianCity::Belovo => println!("Belovo"),
        RussianCity::AnzheroSudzhensk => println!("AnzheroSudzhensk"),
        RussianCity::Chekhov => println!("Chekhov"),
        RussianCity::Vsevolozhsk => println!("Vsevolozhsk"),
        RussianCity::VerkhnyayaPyshma => println!("VerkhnyayaPyshma"),
        RussianCity::Georgiyevsk => println!("Georgiyevsk"),
        RussianCity::Tuymazy => println!("Tuymazy"),
        RussianCity::Minusinsk => println!("Minusinsk"),
        RussianCity::SosnovyBor => println!("SosnovyBor"),
        RussianCity::Kstovo => println!("Kstovo"),
        RussianCity::Dmitrov => println!("Dmitrov"),
        RussianCity::Belogorsk => println!("Belogorsk"),
        RussianCity::Stupino => println!("Stupino"),
        RussianCity::Gukovo => println!("Gukovo"),
        RussianCity::Kungur => println!("Kungur"),
        RussianCity::SlavyansknaKubani => println!("SlavyansknaKubani"),
        RussianCity::Beloretsk => println!("Beloretsk"),
        RussianCity::PavlovskyPosad => println!("PavlovskyPosad"),
        RussianCity::Ishimbay => println!("Ishimbay"),
        RussianCity::Ishim => println!("Ishim"),
        RussianCity::Vidnoye => println!("Vidnoye"),
        RussianCity::Zarechny => println!("Zarechny"),
        RussianCity::Kogalym => println!("Kogalym"),
        RussianCity::Asbest => println!("Asbest"),
        RussianCity::Buynaksk => println!("Buynaksk"),
        RussianCity::Volsk => println!("Volsk"),
        RussianCity::Donskoy => println!("Donskoy"),
        RussianCity::GornoAltaysk => println!("GornoAltaysk"),
        RussianCity::Leninogorsk => println!("Leninogorsk"),
        RussianCity::Rossosh => println!("Rossosh"),
        RussianCity::Tuapse => println!("Tuapse"),
        RussianCity::Klintsy => println!("Klintsy"),
        RussianCity::Budyonnovsk => println!("Budyonnovsk"),
        RussianCity::Borisoglebsk => println!("Borisoglebsk"),
        RussianCity::Revda => println!("Revda"),
        RussianCity::Lysva => println!("Lysva"),
        RussianCity::Zelenogorsk => println!("Zelenogorsk"),
        RussianCity::Polevskoy => println!("Polevskoy"),
        RussianCity::NaroFominsk => println!("NaroFominsk"),
        RussianCity::Kotlas => println!("Kotlas"),
        RussianCity::Sibay => println!("Sibay"),
        RussianCity::Labinsk => println!("Labinsk"),
        RussianCity::Kumertau => println!("Kumertau"),
        RussianCity::Chistopol => println!("Chistopol"),
        RussianCity::Fryazino => println!("Fryazino"),
        RussianCity::Rzhev => println!("Rzhev"),
        RussianCity::Lesosibirsk => println!("Lesosibirsk"),
        RussianCity::Alexandrov => println!("Alexandrov"),
        RussianCity::Belebey => println!("Belebey"),
        RussianCity::Tikhoretsk => println!("Tikhoretsk"),
        RussianCity::Shuya => println!("Shuya"),
        RussianCity::UrusMartan => println!("UrusMartan"),
        RussianCity::Meleuz => println!("Meleuz"),
        RussianCity::Mikhaylovka => println!("Mikhaylovka"),
        RussianCity::Aleksin => println!("Aleksin"),
        RussianCity::Salsk => println!("Salsk"),
        RussianCity::Pavlovo => println!("Pavlovo"),
        RussianCity::Izberbash => println!("Izberbash"),
        RussianCity::Vorkuta => println!("Vorkuta"),
        RussianCity::Shchyokino => println!("Shchyokino"),
        RussianCity::Tikhvin => println!("Tikhvin"),
        RussianCity::Prokhladny => println!("Prokhladny"),
        RussianCity::Nyagan => println!("Nyagan"),
        RussianCity::Lytkarino => println!("Lytkarino"),
        RussianCity::Krasnoturyinsk => println!("Krasnoturyinsk"),
        RussianCity::Krymsk => println!("Krymsk"),
        RussianCity::Neryungri => println!("Neryungri"),
        RussianCity::Beryozovsky => println!("Beryozovsky"),
        RussianCity::Iskitim => println!("Iskitim"),
        RussianCity::Apatity => println!("Apatity"),
        RussianCity::GusKhrustalny => println!("GusKhrustalny"),
        RussianCity::Dzerzhinsky => println!("Dzerzhinsky"),
        RussianCity::Volzhsk => println!("Volzhsk"),
        RussianCity::Zhigulyovsk => println!("Zhigulyovsk"),
        RussianCity::Liski => println!("Liski"),
        RussianCity::Svobodny => println!("Svobodny"),
        RussianCity::Krasnokamsk => println!("Krasnokamsk"),
        RussianCity::Vyksa => println!("Vyksa"),
        RussianCity::Vyazma => println!("Vyazma"),
        RussianCity::Shali => println!("Shali"),
        RussianCity::Krasnokamensk => println!("Krasnokamensk"),
        RussianCity::Arsenyev => println!("Arsenyev"),
        RussianCity::Solnechnogorsk => println!("Solnechnogorsk"),
        RussianCity::Timashyovsk => println!("Timashyovsk"),
        RussianCity::Belorechensk => println!("Belorechensk"),
        RussianCity::Kirishi => println!("Kirishi"),
        RussianCity::Uzlovaya => println!("Uzlovaya"),
        RussianCity::Gudermes => println!("Gudermes"),
        RussianCity::Sertolovo => println!("Sertolovo"),
        RussianCity::Cheremkhovo => println!("Cheremkhovo"),
        RussianCity::Severomorsk => println!("Severomorsk"),
        RussianCity::Borovichi => println!("Borovichi"),
        RussianCity::Roslavl => println!("Roslavl"),
        RussianCity::Snezhinsk => println!("Snezhinsk"),
        RussianCity::Nazarovo => println!("Nazarovo"),
    }
}


```
[Rust Playground](https://play.rust-lang.org/?gist=0c0cdf262f9d8c87a7fae64a93a83d4b&version=stable&mode=debug&edition=2015)

Возможно, имеено так выглядят настоящие полезные программы.

### Домашнее задание
Напишите своё решение сложной задачи - опишите работающее решение сначала в виде констант, а потом напишите его с помощью 
языковой конструкции `enum`.

Попробуйте сконвертировать перечисление в какой-нибудь примитивный формат. Изучите сообщения компилятора.

## Конструкция match

Кострукция `match` отлично подходит для работы с перечислениями. Обратите внимание, что значение для сравнения не обрамляется
скобками (также как и `if`, `while`). Далее следует блок. В нём перечисляются варианты за которыми следуюет `=>`. Далее следует 
выражение. Обратите внимание, что последнее выражение не заключено в фигурные скобки. Так можно написать, так как макрос `println!` возвращает пустой картеж. По этому поводу напишем поясняющий пример кода:
```rust
fn main() {
    #[allow(dead_code)]
    #[derive(Debug)]
    enum ABC {
        A,
        B,
        C,
    }
    let value = println!("{:?}", ABC::A);
    println!("{:?}", value);
    match value {
        () => if true {println!("ok");} 
    }
}


```
[Rust Playground](https://play.rust-lang.org/?gist=e77fce4468195408d554efc738d27873&version=stable&mode=debug&edition=2015)

### Домашнее  задание 
Попробуйте испльзовать перечисление в операторах сравнения `if`,  циклах `while`, `for`.

```rust
fn main() {
    #[allow(dead_code)]
    #[derive(Debug)]
    enum ABC {
        A,
        B,
        C,
    }
    //if  ABC::A == ABC::A {println!("true");}
    //if  ABC::A > ABC::B {println!("true");} else {println!("false");}
}

```
[Rust Playground](https://play.rust-lang.org/?gist=29ad4a634d49cb45a4142790382b9167&version=stable&mode=debug&edition=2015)

### match. Специальный символ `_` 
В случае если необходимы выбрать все остальные вариатны ветвлений `match` - используйте специальный символ `_`. Это своеобразная "заглушка".
```rust
fn main() {
    #[allow(dead_code)]
    #[derive(Debug)]
    enum ABC {
        A,
        B,
        C,
        D,
    }
    let value = ABC::C;
    match value {
        ABC::A => println!("A"),
        ABC::B => println!("B"),
        _ => println!("D"),
    }
}
```
[Rust Playground](https://play.rust-lang.org/?gist=cbd19745fac0552f95f9de843c796e7d&version=stable&mode=debug&edition=2015)

### match и примитивные типы данных
В конструкции `match` могут быть различные типы данных. В том числе примитивные типы данных. Проверим:

```rust
fn main() {
    let value = 1;
    match value {
        0 => println!("A"),
        1 => println!("B"),
        _ => println!("D"),
    }

    let value = true;

    #[allow(unreachable_patterns)]
    match value {
        true => println!("A"),
        false => println!("B"),
        _ => println!("D"),
    }

    let value = 'c';
    match value {
        't' => println!("A"),
        'f' => println!("B"),
        _ => println!("D"),
    }

// а вот и огнаничения. Нельзя использовать дробные числа в match
    let value = 0.;
    #[allow(illegal_floating_point_literal_pattern)]
    match value {
        1. => println!("A"),
        0. => println!("floating B"),
        _ => println!("floating D"),
    }
    
    let value = "0.";
    match value {
        "1." => println!("A"),
        "2." => println!("B"),
        _ => println!("D"),
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=8cf6e1cae2da36df5bca9c394bf6c2cb&version=stable&mode=debug&edition=2015)

## match и enum с входящими значениями

`enum` могут быть достаточно сложны - каждый элемент может иметь свой набор входных данных, благодаря чему можно создавать более сложные и информативные аналитические структуры:
```rust
fn main() {
    #[allow(dead_code)]
    enum Country {
        Russia(f64, char),
        USA(u16, char),
        China,
    }

    let country = Country::USA(1200, 'X');
    match country {
        Country::Russia(value, id) => print!("Result: {}. {}", value, id),
        Country::USA(error_code, module) => print!("Error n. {} in module {}", error_code, module),
        Country::China => {}
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=b89b7d44948a765510bd82af7dbeffed&version=stable&mode=debug&edition=2015)

### Домашнее задание
Напишите свою сложную `enum`. Научитесь пользоваться переменными элементов перечислений.

### Неиспользование переменных
Если по какой-либо причине в переменной перечисления нет необходимости, но код менять нельзя (по какой-то причине), то данную 
переменную можно опустить с помощью специального символа `_`:

```rust
fn main() {
    #[allow(dead_code)]
    enum Country {
        Russia(f64, char),
        USA(u16, char),
        China,
    }
    let country = Country::USA(1200, 'X');
    {
        match country {
            Country::Russia(value, _) => println!("Result: {}", value),
            Country::USA(_, _) => println!("Error."),
            Country::China => {}
        }
    }
    {
        match country {
            Country::Russia(value, id) => println!("Result: id = {}, {}", id, value),
            Country::USA(error_code, module) => {
                println!("Error n. {} in module {}", error_code, module)
            }
            Country::China => {}
        }
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=a198d24ba730b4697930ba07dd057f95&version=stable&mode=debug&edition=2015)

## Использование выражения match
Так как `match`, как и `if` и другие языковые конструкция-выражения (т.е. те, которые возвращают результат своей работы, её
можно использовать для вычисления значения (т.е. как анонимную функцию).

Например:
```rust
fn main() {
    #[allow(dead_code)]
    enum CountrySize {
        Big,
        Small,
        Little,
    }
    let direction = CountrySize::Small;
    print!(
        "{}",
        match direction {
            CountrySize::Big => 'B',
            CountrySize::Small => 'S',
            _ => '*',
        }
    );
}
```
[Rust Playground](https://play.rust-lang.org/?gist=4b9ddb2a33e0690afae6731fbe4ffe58&version=stable&mode=debug&edition=2015)

### Интеллектуальный match
`match` может иметь более тонкую настройку, если требуется учесть  дополнительные обстоятельства. Например,

```rust
fn main() {
    for n in -10..41 {
        println!(
            "{} is {}.",
            n,
            match n {
                0 => "0",
                1 => "one item",
                _ if n < 0 => "negative item",
                _ => "other",
            }
        );
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=5b0a6f01a9549c42e976dcaace5d8238&version=stable&mode=debug&edition=2015)

В данном примере мы видим, что каждый элемент `match` может повторяться и проверять какие-либо ещё условия:
```rust
fn main() {
    for m in 1..10 {
        for n in -10..41 {
            println!(
                "{} is {}.",
                n,
                match n {
                    0 if m == 2 => "0 two",
                    0 if m == 6 => "0 six",
                    0 => "0",
                    1 if m == 3 => "one item three",
                    1 if m == 5 => "one item five",
                    1 => "one",
                    _ if n < 0 => "negative item",
                    _ => "other",
                }
            );
        }
    }
}

```
[Rust Playground](https://play.rust-lang.org/?gist=0c0d498773b1a8f6801b838e0e8de5e1&version=stable&mode=debug&edition=2015)

#### Домашнее задание
Напишите свой вариант использования `match`.
