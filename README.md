#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
typedef struct station 
{
    int prevdist;
    int nextdist;
    int stnid;
    int junc;
    int line;
    char stnname[50];
    char stncode[50];
    struct station *prevstn;
    struct station *nextstn;
} stn;
typedef struct 
{
    int prevdist;
    int nextdist;
    int stnid;
    int junc;
    int line;
    char stnname[50];
    char stncode[50];
} StationData;
stn *head = NULL;
StationData sealdah_lalgola_stations[] = {
    {0, 7, 100, 1, 1, "Sealdah", "SDAH"},
    {7, 5, 101, 0, 1, "Bidhan Nagar", "BNXR"},
    {5, 5, 102, 1, 1, "Dum Dum", "DDJ"},
    {5, 3, 103, 0, 1, "Belgharia", "BLH"},
    {3, 3, 104, 0, 1, "Agarpara", "AGP"},
    {3, 4, 105, 0, 1, "Sodpur", "SEP"},
    {4, 3, 106, 0, 1, "Khardaha", "KDH"},
    {3, 4, 107, 0, 1, "Titagarh", "TGH"},
    {4, 3, 108, 0, 1, "Barrackpore", "BP"},
    {3, 3, 109, 0, 1, "Palta", "PTF"},
    {3, 4, 110, 0, 1, "Ichhapur", "IP"},
    {4, 5, 111, 0, 1, "Shyamnagar", "SNR"},
    {5, 11, 112, 0, 1, "Kankinara", "KNR"},
    {11, 5, 113, 1, 1, "Naihati Jn", "NH"},
    {5, 4, 114, 0, 1, "Halisahar", "HLR"},
    {4, 4, 115, 0, 1, "Kanchrapara", "KPA"},
    {4, 5, 116, 0, 1, "Kalyani", "KYI"},
    {5, 4, 117, 0, 1, "Madanpur", "MPJ"},
    {4, 3, 118, 0, 1, "Simurali", "SMX"},
    {3, 3, 119, 0, 1, "Palpara", "PXR"},
    {3, 5, 120, 0, 1, "Chakdaha", "CDH"},
    {5, 6, 121, 0, 1, "Payradanga", "PDX"},
    {6, 0, 122, 1, 1, "Ranaghat Jn", "RHA"},
    {4, 4, 123, 1, 1, "Kalinaraynpur Jn", "KLNP"},
    {4, 3, 124, 0, 1, "Birnagar", "BIJ"},
    {3, 5, 125, 0, 1, "Taherpur", "THP"},
    {5, 10, 126, 0, 1, "Badkulla", "BDZ"},
    {10, 7, 127, 1, 1, "Krishnanagar City Jn", "KNJ"},
    {7, 5, 128, 0, 1, "Bahadurpur", "BPD"},
    {5, 6, 129, 0, 1, "Dhubulia", "DHU"},
    {6, 10, 130, 0, 1, "Muragacha", "MGM"},
    {10, 4, 131, 0, 1, "Bethuadahari", "BTY"},
    {4, 8, 132, 0, 1, "Sonadanga", "SVH"},
    {8, 4, 133, 0, 1, "Debagram", "DEB"},
    {4, 6, 134, 0, 1, "Pagla Chandi", "PCX"},
    {6, 5, 135, 0, 1, "Plassey", "PLY"},
    {5, 4, 136, 0, 1, "Sirajnagar", "SRJN"},
    {4, 9, 137, 0, 1, "Rejinagar", "REJ"},
    {9, 6, 138, 0, 1, "Beldanga", "BEB"},
    {6, 3, 139, 0, 1, "Bhabta", "BFT"},
    {3, 9, 140, 0, 1, "Saragchni", "SGV"},
    {9, 4, 141, 0, 1, "Berhampore Crt", "BPC"},
    {4, 7, 142, 0, 1, "Cossimbazar", "CSZ"},
    {7, 7, 143, 0, 1, "Murshidabad", "MBB"},
    {5, 7, 144, 0, 1, "Subamamrigi", "SBNM"},
    {7, 4, 145, 0, 1, "Bhagwangola", "BQG"},
    {4, 6, 146, 0, 1, "Pirtala", "PRTL"},
    {6, 1, 147, 0, 1, "Krishnapur", "KRP"},
    {1, 0, 148, 0, 1, "Lalgola", "LGL"}
};

int sealdah_lalgola_count = sizeof(sealdah_lalgola_stations) / sizeof(sealdah_lalgola_stations[0]);
StationData sealdah_burdwan_stations[] = {
    {0, 7, 800, 1, 8, "Sealdah", "SDAH"},
    {7, 5, 801, 0, 8, "Bidhan Nagar", "BNXR"},
    {5, 5, 802, 1, 8, "Dum Dum", "DDJ"},
    {5, 3, 803, 0, 8, "Belgharia", "BLH"},
    {3, 3, 804, 0, 8, "Agarpara", "AGP"},
    {3, 4, 805, 0, 8, "Sodpur", "SEP"},
    {4, 3, 806, 0, 8, "Khardaha", "KDH"},
    {3, 4, 807, 0, 8, "Titagarh", "TGH"},
    {4, 3, 808, 0, 8, "Barrackpore", "BP"},
    {3, 3, 809, 0, 8, "Palta", "PTF"},
    {3, 4, 810, 0, 8, "Ichhapur", "IP"},
    {4, 5, 811, 0, 8, "Shyamnagar", "SNR"},
    {5, 11, 812, 0, 8, "Kankinara", "KNR"},
    {11, 2, 813, 1, 8, "Naihati Jn", "NH"},
    {2, 3, 815, 0, 8, "Garifa", "GFAE"},       
    {3, 2, 814, 0, 8, "Hooghly Ghat", "HYG"},  
    {2, 4, 816, 1, 8, "Bandel Junction", "BDC"},
    {4, 4, 817, 0, 8, "Adisaptagram", "ASP"},
    {4, 5, 818, 0, 8, "Magra", "MGA"},
    {5, 3, 819, 0, 8, "Talandu", "TLD"},
    {3, 4, 820, 0, 8, "Khanyan", "KHN"},
    {4, 5, 821, 0, 8, "Pundooah", "PDA"},
    {5, 3, 822, 0, 8, "Simlagarh", "SLG"},
    {3, 3, 823, 0, 8, "Bainchigram", "BIC"},
    {3, 3, 824, 0, 8, "Bainchi", "BCI"},
    {3, 4, 825, 0, 8, "Debipur", "DBP"},
    {4, 4, 826, 0, 8, "Bagila", "BGL"},
    {4, 4, 827, 0, 8, "Memari", "MME"},
    {4, 3, 828, 0, 8, "Nimo", "NIM"},
    {3, 4, 829, 0, 8, "Rasulpur", "RSP"},
    {4, 3, 830, 0, 8, "Palsit", "PLS"},
    {3, 3, 831, 0, 8, "Saktigarh", "SKT"},
    {3, 5, 832, 0, 8, "Gangpur", "GGP"},
    {5, 0, 833, 1, 8, "Barddhaman Junction", "BWN"}
};

int sealdah_burdwan_count = sizeof(sealdah_burdwan_stations) / sizeof(sealdah_burdwan_stations[0]);
StationData sealdah_katwa_stations[] = {
    {0, 7, 900, 1, 9, "Sealdah", "SDAH"},
    {7, 5, 901, 0, 9, "Bidhan Nagar", "BNXR"},
    {5, 5, 902, 1, 9, "Dum Dum", "DDJ"},
    {5, 3, 903, 0, 9, "Belgharia", "BLH"},
    {3, 3, 904, 0, 9, "Agarpara", "AGP"},
    {3, 4, 905, 0, 9, "Sodpur", "SEP"},
    {4, 3, 906, 0, 9, "Khardaha", "KDH"},
    {3, 4, 907, 0, 9, "Titagarh", "TGH"},
    {4, 3, 908, 0, 9, "Barrackpore", "BP"},
    {3, 3, 909, 0, 9, "Palta", "PTF"},
    {3, 4, 910, 0, 9, "Ichhapur", "IP"},
    {4, 5, 911, 0, 9, "Shyamnagar", "SNR"},
    {5, 11, 912, 0, 9, "Kankinara", "KNR"},
    {11, 5, 913, 1, 9, "Naihati Jn", "NH"},
    {2, 3, 915, 0, 9, "Garifa", "GFAE"},
    {3, 2, 914, 0, 9, "Hooghly Ghat", "HYG"},
    {2, 4, 916, 1, 9, "Bandel Junction", "BDC"},
    {4, 4, 917, 0, 9, "Bansberia", "BSAE"},
    {4, 3, 918, 0, 9, "Tribeni", "TBAE"},
    {3, 2, 919, 0, 9, "Kuntighat", "KGT"},
    {2, 3, 920, 0, 9, "Dumurdaha", "DDH"},
    {3, 2, 921, 0, 9, "Khamargachi", "KMC"},
    {2, 3, 922, 0, 9, "Jirat", "JRT"},
    {3, 2, 923, 0, 9, "Balagarh", "BLGH"},
    {2, 3, 924, 0, 9, "Somrabar Bazaar", "SRBZ"},
    {3, 3, 925, 0, 9, "Behula", "BHU"},
    {3, 4, 926, 0, 9, "Guptipara", "GTP"},
    {4, 3, 927, 0, 9, "Ambika Kalna", "AKL"},
    {3, 4, 928, 0, 9, "Baghnapara", "BGPA"},
    {4, 3, 929, 0, 9, "Dhatrigram", "DTG"},
    {3, 4, 930, 0, 9, "Samudragarh", "SMGD"},
    {4, 3, 931, 0, 9, "Kalinagar", "KLNR"},
    {3, 3, 932, 0, 9, "Nabadwip Dham", "NDAE"},
    {3, 4, 933, 0, 9, "Bishnupriya", "BNPY"},
    {4, 3, 934, 0, 9, "Bhandartikuri", "BDTK"},
    {3, 3, 935, 0, 9, "Purbasthali", "PBST"},
    {3, 3, 936, 0, 9, "Mertala Phaleya", "MTP"},
    {3, 3, 937, 0, 9, "Lakshmipur", "LKPR"},
    {3, 3, 938, 0, 9, "Belerhat", "BLHT"},
    {3, 3, 939, 0, 9, "Patuli", "PTL"},
    {3, 3, 940, 0, 9, "Agradwip", "AGW"},
    {3, 3, 941, 0, 9, "Sahebtala", "SHT"},
    {3, 6, 942, 0, 9, "Dainhat", "DNH"},
    {6, 0, 943, 1, 9, "Katwa Junction", "KWAE"}
};

int sealdah_katwa_count = sizeof(sealdah_katwa_stations) / sizeof(sealdah_katwa_stations[0]);
StationData sealdah_shantipur_stations[] = {
    {0, 7, 200, 1, 2, "Sealdah", "SDAH"},
    {7, 5, 201, 0, 2, "Bidhan Nagar", "BNXR"},
    {5, 5, 202, 1, 2, "Dum Dum", "DDJ"},
    {5, 3, 203, 0, 2, "Belgharia", "BLH"},
    {3, 3, 204, 0, 2, "Agarpara", "AGP"},
    {3, 4, 205, 0, 2, "Sodpur", "SEP"},
    {4, 3, 206, 0, 2, "Khardaha", "KDH"},
    {3, 4, 207, 0, 2, "Titagarh", "TGH"},
    {4, 3, 208, 0, 2, "Barrackpore", "BP"},
    {3, 3, 209, 0, 2, "Palta", "PTF"},
    {3, 4, 210, 0, 2, "Ichhapur", "IP"},
    {4, 5, 211, 0, 2, "Shyamnagar", "SNR"},
    {5, 11, 212, 0, 2, "Kankinara", "KNR"},
    {11, 5, 213, 1, 2, "Naihati Jn", "NH"},
    {5, 4, 214, 0, 2, "Halisahar", "HLR"},
    {4, 4, 215, 0, 2, "Kanchrapara", "KPA"},
    {4, 5, 216, 0, 2, "Kalyani", "KYI"},
    {5, 4, 217, 0, 2, "Madanpur", "MPJ"},
    {4, 3, 218, 0, 2, "Simurali", "SMX"},
    {3, 3, 219, 0, 2, "Palpara", "PXR"},
    {3, 5, 220, 0, 2, "Chakdaha", "CDH"},
    {5, 6, 221, 0, 2, "Payradanga", "PDX"},
    {6, 0, 222, 1, 2, "Ranaghat Jn", "RHA"},
    {4, 4, 223, 1, 2, "Kalinaraynpur Jn", "KLNP"},
    {4, 5, 224, 0, 2, "Habibpur", "HBE"},
    {5, 4, 225, 0, 2, "Phulia", "FLU"},
    {4, 3, 226, 0, 2, "Bathna Krittibas Halt", "BTKB"},
    {3, 0, 227, 0, 2, "Shantipur", "STB"}
};

int sealdah_shantipur_count = sizeof(sealdah_shantipur_stations) / sizeof(sealdah_shantipur_stations[0]);
StationData sealdah_gede_stations[] = {
    {0, 7, 300, 1, 3, "Sealdah", "SDAH"},
    {7, 3, 301, 0, 3, "Bidhan Nagar", "BNXR"},
    {3, 4, 302, 1, 3, "Dum Dum", "DDJ"},
    {4, 4, 303, 0, 3, "Belgharia", "BLH"},
    {4, 2, 304, 0, 3, "Agarpara", "AGP"},
    {2, 2, 305, 0, 3, "Sodpur", "SEP"},
    {2, 2, 306, 0, 3, "Khardaha", "KDH"},
    {2, 2, 307, 0, 3, "Titagarh", "TGH"},
    {2, 2, 308, 0, 3, "Barrackpore", "BP"},
    {2, 2, 309, 0, 3, "Palta", "PTF"},
    {2, 2, 310, 0, 3, "Ichhapur", "IP"},
    {2, 3, 311, 0, 3, "Shyamnagar", "SNR"},
    {3, 2, 312, 0, 3, "Jagadal", "JGDL"},
    {2, 3, 313, 0, 3, "Kankinara", "KNR"},
    {3, 4, 314, 1, 3, "Naihati Jn", "NH"},
    {4, 3, 315, 0, 3, "Halisahar", "HLR"},
    {3, 3, 316, 0, 3, "Kanchrapara", "KPA"},
    {3, 5, 317, 0, 3, "Kalyani", "KYI"},
    {5, 4, 318, 0, 3, "Madanpur", "MPJ"},
    {4, 2, 319, 0, 3, "Simurali", "SMX"},
    {2, 2, 320, 0, 3, "Palpara", "PXR"},
    {2, 6, 321, 0, 3, "Chakdaha", "CDH"},
    {6, 5, 322, 0, 3, "Payradanga", "PDX"},
    {5, 5, 323, 1, 3, "Ranaghat Jn", "RHA"},
    {5, 1, 324, 0, 3, "Bankim Nagar", "BNKA"},
    {1, 3, 325, 0, 3, "Pancheberia", "PNCB"},
    {3, 4, 326, 0, 3, "Aranghata", "AG"},
    {4, 5, 327, 0, 3, "Bhairgachhi", "BHGH"},
    {5, 4, 328, 0, 3, "Bhayna", "BHNA"},
    {4, 3, 329, 0, 3, "Bagula", "BGL"},
    {3, 3, 330, 0, 3, "Mayurhat", "MYHT"},
    {3, 3, 331, 0, 3, "Tarak Nagar", "TNX"},
    {3, 4, 332, 0, 3, "Majhdia", "MIJ"},
    {4, 6, 333, 0, 3, "Banpur", "BPN"},
    {6, 3, 334, 0, 3, "Harish Nagar Halt", "HRSR"},
    {3, 0, 335, 0, 3, "Gede", "GEDE"}
};

int sealdah_gede_count = sizeof(sealdah_gede_stations) / sizeof(sealdah_gede_stations[0]);
StationData sdah_bongaon_stations[] = {
    {0, 7, 500, 1, 5, "Sealdah",               "SDAH"},
    {7, 3, 501, 0, 5, "Bidhan Nagar",          "BNXR"},
    {3, 3, 502, 1, 5, "Dum Dum",               "DDJ"},
    {3, 3, 503, 0, 5, "Dum Dum Cant",          "DDC"},
    {3, 2, 504, 0, 5, "Durganagar",            "DGNR"},
    {2, 1, 505, 0, 5, "Birati",                "BBT"},
    {1, 2, 506, 0, 5, "Bisharpara Kodaliya",   "BRPK"},
    {2, 1, 507, 0, 5, "New Barrackpore",       "NBE"},
    {1, 2, 508, 0, 5, "Madhyamgram",           "MMG"},
    {2, 2, 509, 0, 5, "Hridaypur",             "HHR"},
    {2, 7, 510, 1, 5, "Barasat",               "BT"},
    {7, 4, 511, 0, 5, "Bamangachhi",           "BMG"},
    {4, 4, 512, 0, 5, "Dattapukur",            "DTK"},
    {4, 4, 513, 0, 5, "Bira",                  "BIRA"},
    {4, 3, 514, 0, 5, "Guma",                  "GUMA"},
    {3, 4, 515, 0, 5, "Ashok Nagar Road",      "ASKR"},
    {4, 3, 516, 0, 5, "Habra",                 "HB"},
    {3, 5, 517, 0, 5, "Sanhati",               "SNHT"},
    {5, 4, 518, 0, 5, "Machhalandapur",        "MSL"},
    {4, 4, 519, 0, 5, "Gobardanga",            "GBG"},
    {4, 5, 520, 0, 5, "Thakurnagar",           "TKNR"},
    {5, 4, 521, 0, 5, "Chandpara",             "CDP"},
    {4, 5, 522, 0, 5, "Bibhuti Bhushan Halt",  "BNAA"},
    {5, 0, 523, 1, 5, "Bangaon Jn",            "BNJ"}
};

int sdah_bongaon_count = sizeof(sdah_bongaon_stations) / sizeof(sdah_bongaon_stations[0]);
StationData sdah_hasnabad_stations[] = {
    {0, 7, 600, 1, 6, "Sealdah",               "SDAH"},
    {7, 1, 601, 0, 6, "Bidhan Nagar",          "BNXR"},
    {1, 1, 602, 1, 6, "Dum Dum",               "DDJ"},
    {1, 1, 603, 0, 6, "Dum Dum Cant",          "DDC"},
    {1, 1, 604, 0, 6, "Durganagar",            "DGNR"},
    {1, 1, 605, 0, 6, "Birati",                "BBT"},
    {1, 2, 606, 0, 6, "Bisharpara Kodaliya",   "BRPK"},
    {2, 1, 607, 0, 6, "New Barrackpore",       "NBE"},
    {1, 2, 608, 0, 6, "Madhyamgram",           "MMG"},
    {2, 2, 609, 0, 6, "Hridaypur",             "HHR"},
    {2, 7, 610, 1, 6, "Barasat",               "BT"},
    {7, 1, 611, 0, 6, "Kazipara",              "KZPR"},
    {1, 4, 612, 0, 6, "Karea Kadambagachi",    "KBGH"},
    {4, 3, 613, 0, 6, "Bahira Kalibari",       "BHKA"},
    {3, 4, 614, 0, 6, "Sondalia",              "SXC"},
    {4, 3, 615, 0, 6, "Beliaghata Road",       "BGRD"},
    {3, 4, 616, 0, 6, "Lebutala",              "LBTL"},
    {4, 2, 617, 0, 6, "Bhasila",               "BSLA"},
    {2, 4, 618, 0, 6, "Harua Road",            "HRO"},
    {4, 3, 619, 0, 6, "Kankara Mirzanagar",    "KMZA"},
    {3, 5, 620, 0, 6, "Malatipur",             "MPE"},
    {5, 3, 621, 0, 6, "Ghovarash Ghona",       "GGV"},
    {3, 2, 622, 0, 6, "Champapukur",           "CQR"},
    {2, 5, 623, 0, 6, "Bhyabla Halt",          "BBLA"},
    {5, 1, 624, 0, 6, "Basirhat",              "BSHT"},
    {1, 5, 625, 0, 6, "Madhyampur",            "MPN"},
    {5, 2, 626, 0, 6, "Nimdanri",              "NMDR"},
    {2, 2, 627, 0, 6, "Taki Road",             "TKF"},
    {2, 0, 628, 1, 6, "Hasanabad",             "HNB"}
};

int sdah_hasnabad_count = sizeof(sdah_hasnabad_stations) / sizeof(sdah_hasnabad_stations[0]);
StationData sdah_dankuni_stations[] = {
    { 0,  7, 400, 1, 4, "Sealdah",          "SDAH" },
    { 7,  3, 401, 0, 4, "Bidhan Nagar",     "BNXR" },
    { 3,  5, 402, 1, 4, "Dum Dum",          "DDJ" },
    { 5,  1, 403, 0, 4, "Baranagar Road",   "BARN" },
    { 1,  2, 404, 0, 4, "Dakshineswar",     "DAKE" },
    { 2,  2, 405, 0, 4, "Bally Ghat",       "BLYG" },
    { 2,  4, 406, 0, 4, "Ballyhalt",        "BLYH" },
    { 4,  2, 407, 0, 4, "Rajchandrapur",    "RCD" },
    { 2,  0, 408, 1, 4, "Dankuni",          "DKAE" }
};

int sdah_dankuni_count = sizeof(sdah_dankuni_stations) / sizeof(sdah_dankuni_stations[0]);
StationData rna_bgn_stations[] = {
    { 0,   6,  1, 1, 7, "Ranaghat Jn", "RHA" },
    { 6,   4,  2, 0, 7, "Naba Raynagar Halt", "NBRN" },
    { 4,   4,  3, 0, 7, "Gangnapur", "GGP" },
    { 4,   4,  4, 0, 7, "Majhergram", "MAJ" },
    { 4,   4,  5, 0, 7, "Akaipur Halt", "AKIP" },
    { 4,   5,  6, 0, 7, "Gopal Nagar", "GN" },
    { 5,   5,  7, 0, 7, "Satberia", "STBB" },
    { 5,   0,  8, 1, 7, "Bangaon Jn", "BNJ" }
};
int rna_bgn_count = sizeof(rna_bgn_stations) / sizeof(rna_bgn_stations[0]);
StationData sdah_canning_stations[] = {
    { 0, 3, 1000, 1, 10, "Sealdah",               "SDAH" },
    { 3, 2, 1001, 0, 10, "Park Circus",           "PQS" },
    { 2, 1, 1002, 1, 10, "Ballygunge Jn",         "BLN" },
    { 1, 2, 1003, 0, 10, "Dhakuria",              "DHK" },
    { 2, 2, 1004, 0, 10, "Jadavpur",              "JDP" },
    { 2, 2, 1005, 0, 10, "Bagha Jatin",           "BGJT" },
    { 2, 4, 1006, 0, 10, "Garia",                 "GIA" },
    { 4, 3, 1007, 1, 10, "Sonarpur Jn",           "SPR" },
    { 3, 3, 1008, 0, 10, "Bidyadharpur",          "BDYP" },
    { 3, 2, 1009, 0, 10, "Kalikapur",             "KLKR" },
    { 2, 3, 1010, 0, 10, "Champahati",            "CHT" },
    { 3, 1, 1011, 0, 10, "Piali",                 "PLF" },
    { 1, 3, 1012, 0, 10, "Gourdaha (Halt)",       "GQD" },
    { 3, 3, 1013, 0, 10, "Ghutiari Sharif",       "GOF" },
    { 3, 4, 1014, 0, 10, "Bethberia Ghola",       "BTPG" },
    { 4, 7, 1015, 0, 10, "Taldi",                 "TLX" },
    { 7, 0, 1016, 0, 10, "Canning",               "CG" }
};

int sdah_canning_count = sizeof(sdah_canning_stations) / sizeof(sdah_canning_stations[0]);
StationData sdah_diamond_stations[] = {
    { 0, 3, 1100, 1, 11, "Sealdah",                  "SDAH" },
    { 3, 2, 1101, 0, 11, "Park Circus",              "PQS" },
    { 2, 1, 1102, 1, 11, "Ballygunge Jn",            "BLN" },
    { 1, 2, 1103, 0, 11, "Dhakuria",                 "DHK" },
    { 2, 2, 1104, 0, 11, "Jadavpur",                 "JDP" },
    { 2, 2, 1105, 0, 11, "Bagha Jatin",              "BGJT" },
    { 2, 2, 1106, 0, 11, "Garia",                    "GIA" },
    { 2, 2, 1107, 0, 11, "Narendrapur Halt",         "NRPR" },
    { 2, 4, 1108, 1, 11, "Sonarpur Jn",              "SPR" },
    { 4, 2, 1109, 0, 11, "Subhas Gram",              "SBGR" },
    { 2, 3, 1110, 0, 11, "Mallikpur",                "MAK" },
    { 3, 3, 1111, 1, 11, "Baruipur Junction",        "BRP" },
    { 3, 2, 1112, 0, 11, "Kalyanpur",                "KYP" },
    { 2, 2, 1113, 0, 11, "Dakshin Durgapur",         "DKDP" },
    { 2, 2, 1114, 0, 11, "Hotar",                     "HT" },
    { 2, 3, 1115, 0, 11, "Dhamua",                   "DMU" },
    { 3, 3, 1116, 0, 11, "Uttar Radhanagar Halt",    "UTN" },
    { 3, 3, 1117, 0, 11, "Magra Hat",                "MGT" },
    { 3, 2, 1118, 0, 11, "Bahrupiya Halt",           "BHPA" },
    { 2, 5, 1119, 0, 11, "Sangrampur",               "SNU" },
    { 5, 3, 1120, 0, 11, "Deula",                    "D" },
    { 3, 2, 1121, 0, 11, "Netra",                    "NTA" },
    { 2, 2, 1122, 0, 11, "Basuldanga",               "BSD" },
    { 2, 3, 1123, 0, 11, "Gurudas Nagar",            "GURN" },
    { 3, 0, 1124, 0, 11, "Diamond Harbour",          "DH" }
};

int sdah_diamond_count = sizeof(sdah_diamond_stations) / sizeof(sdah_diamond_stations[0]);
StationData sdah_namkhana_stations[] = {
    { 0, 3, 1200, 1, 12, "Sealdah",                     "SDAH" },
    { 3, 2, 1201, 0, 12, "Park Circus",                 "PQS" },
    { 2, 1, 1202, 1, 12, "Ballygunge Jn",               "BLN" },
    { 1, 2, 1203, 0, 12, "Dhakuria",                    "DHK" },
    { 2, 1, 1204, 0, 12, "Jadavpur",                    "JDP" },
    { 1, 2, 1205, 0, 12, "Bagha Jatin",                 "BGJT" },
    { 2, 1, 1206, 0, 12, "New Garia",                   "NGRI" },
    { 1, 2, 1207, 0, 12, "Garia",                       "GIA" },
    { 2, 2, 1208, 0, 12, "Narendrapur Halt",            "NRPR" },
    { 2, 3, 1209, 1, 12, "Sonarpur Jn",                 "SPR" },
    { 3, 2, 1210, 0, 12, "Subhas Gram",                 "SBGR" },
    { 2, 4, 1211, 0, 12, "Mallikpur",                   "MAK" },
    { 4, 2, 1212, 1, 12, "Baruipur Junction",           "BRP" },
    { 2, 2, 1213, 0, 12, "Shasan Road",                 "SSRD" },
    { 2, 2, 1214, 0, 12, "Krishnamohan Halt",           "KRXM" },
    { 2, 3, 1215, 0, 12, "Dhapdhapi",                   "DPDP" },
    { 3, 2, 1216, 0, 12, "Surjyapur",                   "SJPR" },
    { 2, 2, 1217, 0, 12, "Gocharan",                    "GCN" },
    { 2, 4, 1218, 0, 12, "Hogla",                        "HGA" },
    { 4, 2, 1219, 0, 12, "Dakshin Barasat",             "DBT" },
    { 2, 5, 1220, 0, 12, "Baharu",                       "BARU" },
    { 5, 5, 1221, 0, 12, "Jayanagar Majlipur Halt",     "JNM" },
    { 5, 4, 1222, 0, 12, "Mathurapur Road",             "MPRD" },
    { 4, 3, 1223, 0, 12, "Madhabpur",                   "MDBP" },
    { 3, 6, 1224, 0, 12, "Lakshmikantpur",              "LKPR" },
    { 6, 4, 1225, 0, 12, "Udairampur",                  "URP" },
    { 4, 4, 1226, 0, 12, "Kulpi Flag",                  "KLW" },
    { 4, 8, 1227, 0, 12, "Karanjali",                   "KNJI" },
    { 8, 9, 1228, 0, 12, "Nishchindapur",               "NCP" },
    { 9, 3, 1229, 0, 12, "Kashinagar Halt",             "KHGR" },
    { 3, 13, 1230, 0, 12, "Kakdwip",                     "KWDP" },
    { 13, 0, 1231, 0, 12, "Namkhana",                    "NMKA" }
};

int sdah_namkhana_count = sizeof(sdah_namkhana_stations) / sizeof(sdah_namkhana_stations[0]);
stn* build_station_list(StationData *data, int count) 
{
    stn *head = NULL;
    stn *prev = NULL;

    for (int i = 0; i < count; i++) 
	{
        stn *newstn = (stn*) malloc(sizeof(stn));
        if (!newstn) 
		{
            printf("Memory allocation failed!\n");
            exit(1);
        }
        newstn->prevdist = data[i].prevdist;
        newstn->nextdist = data[i].nextdist;
        newstn->stnid = data[i].stnid;
        newstn->junc = data[i].junc;
        newstn->line = data[i].line;
        strcpy(newstn->stnname, data[i].stnname);
        strcpy(newstn->stncode, data[i].stncode);
        newstn->prevstn = prev;
        newstn->nextstn = NULL;

        if (prev)
            prev->nextstn = newstn;
        else
            head = newstn;  // Set head to first station

        prev = newstn;
    }
    return head;
}
StationData* find_station_by_name(const char* name) 
{
    for (int i = 0; i < sealdah_lalgola_count; i++)
        if (strcasecmp(sealdah_lalgola_stations[i].stnname, name) == 0) return &sealdah_lalgola_stations[i];
    for (int i = 0; i < sealdah_burdwan_count; i++)
        if (strcasecmp(sealdah_burdwan_stations[i].stnname, name) == 0) return &sealdah_burdwan_stations[i];
    for (int i = 0; i < sealdah_shantipur_count; i++)
        if (strcasecmp(sealdah_shantipur_stations[i].stnname, name) == 0) return &sealdah_shantipur_stations[i];
    for (int i = 0; i < sealdah_katwa_count; i++)
        if (strcasecmp(sealdah_katwa_stations[i].stnname, name) == 0) return &sealdah_katwa_stations[i];
    for (int i = 0; i < sealdah_gede_count; i++)
        if (strcasecmp(sealdah_gede_stations[i].stnname, name) == 0) return &sealdah_gede_stations[i];
    for (int i = 0; i < sdah_bongaon_count; i++)
        if (strcasecmp(sdah_bongaon_stations[i].stnname, name) == 0) return &sdah_bongaon_stations[i];
    for (int i = 0; i < sdah_hasnabad_count; i++)
        if (strcasecmp(sdah_hasnabad_stations[i].stnname, name) == 0) return &sdah_hasnabad_stations[i];
    for (int i = 0; i < sdah_dankuni_count; i++)
        if (strcasecmp(sdah_dankuni_stations[i].stnname, name) == 0) return &sdah_dankuni_stations[i];
    for (int i = 0; i < rna_bgn_count; i++)
        if (strcasecmp(rna_bgn_stations[i].stnname, name) == 0) return &rna_bgn_stations[i];
    for (int i = 0; i < sdah_canning_count; i++)
        if (strcasecmp(sdah_canning_stations[i].stnname, name) == 0) return &sdah_canning_stations[i];
    for (int i = 0; i < sdah_diamond_count; i++)
        if (strcasecmp(sdah_diamond_stations[i].stnname, name) == 0) return &sdah_diamond_stations[i];
    for (int i = 0; i < sdah_namkhana_count; i++)
        if (strcasecmp(sdah_namkhana_stations[i].stnname, name) == 0) return &sdah_namkhana_stations[i];
    return NULL;
}

int compute_distance_same_line(stn *src, stn *dest)
{
    if (!src || !dest) return -1;

    stn *tmp = src;
    int dist = 0;

    // forward direction
    while (tmp && tmp != dest)
    {
        dist += tmp->nextdist;
        tmp = tmp->nextstn;
    }
    if (tmp == dest) return dist;

    // backward direction
    tmp = src;
    dist = 0;

    while (tmp && tmp != dest)
    {
        dist += tmp->prevdist;
        tmp = tmp->prevstn;
    }
    if (tmp == dest) return dist;

    return -1;
}
stn* find_station_in_list(stn *head, const char *name)
{
    while (head)
    {
        if (strcasecmp(head->stnname, name) == 0)
            return head;
        head = head->nextstn;
    }
    return NULL;
}

//========================================================
//          AUTO INTERLINE CONNECTIVITY (JUNCTION ROUTING)
//========================================================

int compute_interline_distance(StationData *src, StationData *dest)
{
    if (src->line == dest->line)
        return -1; // same line handled earlier

    // List of major junctions that exist in multiple lines
    const char *junctions[] = {
        "Sealdah","Dum Dum","Naihati Jn",
		"Ranaghat Jn","Kalinaraynpur Jn",
		"Krishnanagar City Jn","Bandel Junction","Barddhaman Junction",
		"Katwa Junction","Ballygunge Jn","Sonarpur Jn",
		"Baruipur Junction","Barasat",
		"Bangaon Jn","Hasanabad","Dankuni"
    };

    int jcount = 16;
    int best_dist = 999999;

    for (int i = 0; i < jcount; i++)
    {
        StationData *j = find_station_by_name(junctions[i]);
        if (!j) continue;

        // ---------- Route: SRC ? Junction ----------
        stn *lineA = NULL;
        int Aline = src->line;

        switch (Aline)
        {
            case 1: lineA = build_station_list(sealdah_lalgola_stations, sealdah_lalgola_count); break;
            case 2: lineA = build_station_list(sealdah_shantipur_stations, sealdah_shantipur_count); break;
            case 3: lineA = build_station_list(sealdah_gede_stations, sealdah_gede_count); break;
            case 4: lineA = build_station_list(sdah_bongaon_stations, sdah_bongaon_count); break;
            case 5: lineA = build_station_list(sdah_hasnabad_stations, sdah_hasnabad_count); break;
            case 6: lineA = build_station_list(sdah_dankuni_stations, sdah_dankuni_count); break;
            case 7: lineA = build_station_list(rna_bgn_stations, rna_bgn_count); break;
            case 8: lineA = build_station_list(sealdah_burdwan_stations, sealdah_burdwan_count); break;
            case 9: lineA = build_station_list(sealdah_katwa_stations, sealdah_katwa_count); break;
            case 10: lineA = build_station_list(sdah_canning_stations, sdah_canning_count); break;
            case 11: lineA = build_station_list(sdah_diamond_stations, sdah_diamond_count); break;
            case 12: lineA = build_station_list(sdah_namkhana_stations, sdah_namkhana_count); break;
            default: lineA = NULL; break;
        }

        stn *snode = find_station_in_list(lineA, src->stnname);
        stn *jnode = find_station_in_list(lineA, j->stnname);
        if (!snode || !jnode) continue;

        int dist1 = compute_distance_same_line(snode, jnode);
        if (dist1 < 0) continue;

        // ---------- Route: Junction ? DEST ----------
        stn *lineB = NULL;
        int Bline = dest->line;

        switch (Bline)
        {
            case 1: lineB = build_station_list(sealdah_lalgola_stations, sealdah_lalgola_count); break;
            case 2: lineB = build_station_list(sealdah_shantipur_stations, sealdah_shantipur_count); break;
            case 3: lineB = build_station_list(sealdah_gede_stations, sealdah_gede_count); break;
            case 4: lineB = build_station_list(sdah_bongaon_stations, sdah_bongaon_count); break;
            case 5: lineB = build_station_list(sdah_hasnabad_stations, sdah_hasnabad_count); break;
            case 6: lineB = build_station_list(sdah_dankuni_stations, sdah_dankuni_count); break;
            case 7: lineB = build_station_list(rna_bgn_stations, rna_bgn_count); break;
            case 8: lineB = build_station_list(sealdah_burdwan_stations, sealdah_burdwan_count); break;
            case 9: lineB = build_station_list(sealdah_katwa_stations, sealdah_katwa_count); break;
            case 10: lineB = build_station_list(sdah_canning_stations, sdah_canning_count); break;
            case 11: lineB = build_station_list(sdah_diamond_stations, sdah_diamond_count); break;
            case 12: lineB = build_station_list(sdah_namkhana_stations, sdah_namkhana_count); break;
        }

        stn *jnode2 = find_station_in_list(lineB, j->stnname);
        stn *dnode = find_station_in_list(lineB, dest->stnname);
        if (!jnode2 || !dnode) continue;

        int dist2 = compute_distance_same_line(jnode2, dnode);
        if (dist2 < 0) continue;

        if (dist1 + dist2 < best_dist)
            best_dist = dist1 + dist2;
    }

    return (best_dist == 999999) ? -1 : best_dist;
}
int ticketcalculate(int dist, int r)
{
    int price;
    if (dist <= 20) price = 5;
    else if (dist>20 && dist<=44) price = 10;
    else if (dist>44 && dist <= 60) price = 15;
    else if (dist>60 && dist <= 75) price = 20;
    else if (dist>75 && dist <= 90) price = 25;
    else if (dist>90 && dist <= 110) price = 30;
    else if (dist>110 && dist <= 130) price = 40;
    else if (dist>130 && dist <= 150) price = 50;
    else if (dist>150 && dist <= 180) price = 65;
    else if (dist>180 && dist <= 200) price = 90;
    else if (dist>200 && dist <= 220) price = 100;
    else if (dist>220 && dist <= 240) price = 120;
    else if (dist>240 && dist <= 300) price = 150;
    else price=200;

    if (r == 1) price *= 2;
    return price;
}
void generate_ticket_id(char *out)
{
    srand(time(NULL));
    long t = time(NULL);
    int r = rand() % 90000 + 10000;

    sprintf(out, "TKT-%d-%ld", r, t);
}
void generateticket(const char *source, const char *destination,
                    int dist, int price, int rtype)
{
    char tid[50];
    generate_ticket_id(tid);

    printf("\n----------------------------------------\n");
    printf("        INDIAN RAILWAY TICKET\n");
    printf("----------------------------------------\n");
    printf("Ticket ID    : %s\n", tid);
    printf("From Station : %s\n", source);
    printf("To Station   : %s\n", destination);
    printf("Distance     : %d km\n", dist);
    printf("Trip Type    : %s\n", (rtype ? "Round Trip" : "One Way"));
    printf("Ticket Price : Rs. %d\n", price);
    printf("----------------------------------------\n");
    printf("Thank you for travelling with us!\n");
    printf("----------------------------------------\n\n");
}

int main() 
{
    srand(time(NULL)); // Initialize random seed once

    int t, m, c,more;
    do 
    {
        char src[50], dest[50];
        printf("Enter Source Station: ");
        fgets(src, 50, stdin);
        src[strcspn(src, "\n")] = 0;

        printf("Enter Destination Station: ");
        fgets(dest, 50, stdin);
        dest[strcspn(dest, "\n")] = 0;

        printf("Enter 1 if you want round trip ticket, else 0: ");
        scanf("%d", &t);
        getchar();

        StationData *s = find_station_by_name(src);
        StationData *d = find_station_by_name(dest);

        if (!s || !d) {
            printf("Invalid station entered.\n");
            continue;
        }

        int total_dist = -1;

        // Choose line to build linked list for (chooses bigger line as in original)
        c = (d->line > s->line) ? d->line : s->line;
		if (s->line == d->line)
        {
        switch (c) 
        {
            case 1:
                head = build_station_list(sealdah_lalgola_stations, sealdah_lalgola_count);
                break;
            case 8:
                head = build_station_list(sealdah_burdwan_stations, sealdah_burdwan_count);
                break;
            case 9:
                head = build_station_list(sealdah_katwa_stations, sealdah_katwa_count);
                break;
            case 2:
                head = build_station_list(sealdah_shantipur_stations, sealdah_shantipur_count);
                break;
            case 3:
                head = build_station_list(sealdah_gede_stations, sealdah_gede_count);
                break;
            case 4:
                head = build_station_list(sdah_bongaon_stations, sdah_bongaon_count);
                break;
            case 5:
                head = build_station_list(sdah_hasnabad_stations, sdah_hasnabad_count);
                break;
            case 6:
                head = build_station_list(sdah_dankuni_stations, sdah_dankuni_count);
                break;
            case 7:
                head = build_station_list(rna_bgn_stations, rna_bgn_count);
                break;
            case 10:
                head = build_station_list(sdah_canning_stations, sdah_canning_count);
                break;
            case 11:
                head = build_station_list(sdah_diamond_stations, sdah_diamond_count);
                break;
            case 12:
                head = build_station_list(sdah_namkhana_stations, sdah_namkhana_count);
                break;
            default:
                printf("Sorry... Direct ticket of such route can't be generated.\n");
                head = NULL;
                break;
        }

        	stn *sn = find_station_in_list(head, src);
        	stn *dn = find_station_in_list(head, dest);

            total_dist = compute_distance_same_line(sn, dn);
    	}
        else
        {
            // Interline connectivity
            total_dist = compute_interline_distance(s, d);
        }

        if (total_dist < 0)
        {
            printf("Sorry... No valid route found.\n");
        }
        else
        {
            if (t == 1) total_dist *= 2;

            int price = ticketcalculate(total_dist, 0);
            generateticket(src, dest, total_dist, price, t);
        }

        printf("Generate more tickets? Enter 1: ");
        scanf("%d", &more);
        getchar();
    } while (more == 1);

    return 0;
}

