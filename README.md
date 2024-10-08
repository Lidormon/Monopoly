# Monopoly

This project implements a simplified version of the classic board game Monopoly using QT GUI. The game includes all key components such as players, assets (properties), and game tiles, as well as handling rules and interactions between players. It is designed to simulate a competitive Monopoly game experience with a focus on properties, player management, and error handling.

Project Structure

model: Contains the core classes and logic related to the game model.
view: Handles the user interface or graphical representation of the game (though this depends on the specific contents of the folder).

Files

assets.cpp / assets.h: I am loading the game data from the 'assets' folder, which contains the text files (spaces.txt, colors.txt, chance.txt, community_chest.txt) with the information.  In addition these files manage the game’s assets, such as properties and utilities, including their ownership, purchase price, and rent calculation. Note: if I change the number of tiles on the board (by adding or removing rows in spaces.txt, the 'go to' rows in chance.txt also need to be adjusted.

main.cpp: This is the entry point for the game, responsible for initializing the game components, handling game flow, and managing player turns.

monopoly.cpp / monopoly.h: These files contain the core logic of the game, including rules for buying properties, handling special tiles (e.g., Chance, Go to Jail), and interactions between players. 

monopolyerrors.cpp / monopolyerrors.h: These handle potential errors or exceptions that may arise during gameplay, ensuring the game runs smoothly without crashing.

ownabletilelist.cpp / ownabletilelist.h: These files manage the list of tiles that can be owned by players, such as properties, and utilities.

playerlist.cpp / playerlist.h: These manage the list of players, keeping track of their financial status, properties, and position on the board.



Game Features
  
Player Management: Handles multiple players, including their movement across the board, financial transactions, and asset ownership.

Property Ownership: Implements the core concept of buying, selling, and renting properties.

Game Flow: Enforces the rules of Monopoly, ensuring proper turn-based gameplay, and interaction with special tiles such as "Go to Jail" or "Chance" cards.

Error Handling: Robust error handling to prevent crashes during gameplay, particularly around property transactions and player status.



Rules Of The Game

המשחק מורכב מלוח המכיל 40 משבצות המקיפות אותו, כל משבצת יכולה לייצג רחוב, קווי רכבת, משבצות מיוחדות ועוד. בהמשך נפרט על סוגי המשבצות השונים.
משבצות הלוח
כידוע, הלוח מחולק ל-40 משבצות שונות כאשר בכל משבצת השחקן יכול לבצע פעולות שונות. עליכם לבנות לוח דינאמי המאפשר הוספה של משבצות נוספות למשחק. 
רחובות
משבצת הרחוב שייכת לקבוצת צבע כלשהי מתוך 8 קבוצות צבע אפשריות. לכל רחוב יש שם, מחיר, עלות שכירות, מחיר בית ומחיר שכירות עם בית וגם מחיר שכירות עם מלון. שחקן יכול לבנות בית ברחוב כלשהו רק אם הוא מחזיק בכל הרחובות השייכים לאותה קבוצת הצבע. כאשר שחקן נוחת ברחוב השייך לשחקן אחר הוא מחויב לשלם לו שכירות לפי מה שבנוי באותו הרחוב - אם הרחוב ריק (כלומר ללא בית) השחקן ישלם את מחיר השכירות של אותו הרחוב אבל אם הרחוב מכיל בית השחקן ישלם את השכירות לפי החוקים הבאים: דמי השכירות גדלים פי 2 עם כל בית נוסף. כלומר דמי השכירות הם: דמי השכירות של בית אחד, כפול 2 בחזקת (מספר הבתים פחות 1). אם הרחוב מכיל מלון, השחקן ישלם את דמי השכירות עם המלון. סוגי הצבעים, השמות של הרחובות והמחירים נתונים לשיקול דעתכם.
בניית בתים
כזכור, שחקן יכול לבנות בית ברחוב מסוים רק אם מחזיק בכל הרחובות השייכים לאותה קבוצת צבע. ניתן לרכוש עד 4 בתים לכל רחוב ולאחר מכן גם מלון לפי החוקים הבאים:
    • כדי לקנות בית נוסף, על השחקן לבנות את אותו המספר של בתים בשאר קבוצות הצבע (כלומר, נניח שיש לי 2 רחובות השייכים לאותה קבוצת צבע ובאחד בניתי בית ובשני לא. לא אפשרי לבנות בית נוסף ברחוב הראשון, עד שנבנה בית ברחוב השני).
    • ניתן לבנות בית נוסף במחיר של בית רגיל (כלומר אם עלות בנייה של בית היא 100 שקלים, אז עלות כל בית נוסף גם תהיה 100 שקלים).
    • ניתן לבנות מלון רק אחרי שנבנו 4 בתים באותו הרחוב. מחיר המלון הוא מחירם של 4 בתים + 100 שקלים.
רכבות
במשחק יש 4 רכבות, רכבת אחת בכל צד של הלוח. העלות של כל רכבת היא 200 שקלים. כאשר שחקן נוחת ברכבת של שחקן אחר הוא ישלם לו מס לפי מספר הרכבות של השחקן אצלו נחתו:
    • רכבת אחת - 50 שקלים
    • 2  רכבות - 100 שקלים
    •  3 רכבות - 150 שקלים
    •  4 רכבות - 200 שקלים
משבצות מיוחדות
הלוח מכיל משבצות מיוחדות מסוגים שונים.
    • משבצת הפתעה - אם השחקן נוחת על המשבצת הזאת הוא מקבל איזושהי "הפתעה", למשל כרטיס יציאה מהכלא או זיכוי של כסף לחשבון. על ההפתעות להיות דינאמיות - כלומר כל הזמן ניתן לייצר הפתעות נוספות. לרשותכם דוגמה להפתעות היכולות להופיע במשחק בקובץ monopoly_chance_cards.txt.
    • משבצת "חנייה חופשית" - אם השחקן נוחת במשבצת הזאת הוא מסיים את התור ומעביר אותו לשחקן הבא.
    • משבצות מס - אם השחקן נוחת במשבצות מהסוג הזה הוא משלם מס על סך 100 שקלים.
    • משבצת "לך לכלא" - אם השחקן נוחת על המשבצת הזאת הוא נכנס לכלא ומשחק לפי הכללים של המשבצת הזאת.
    • חברת החשמל וחברת המים - הלוח מכיל 2 משבצות עבור חברת המים וחברת החשמל. עלות על חברה היא 150 שקלים ואם שחקן נוחת במשבצת כזאת שהיא בבעלותו של שחקן אחר, עליו לשלם לאותו שחקן את סכום ההטלה כפול עשר.
הכלא
שחקן יכול להיכנס לכלא רק אם נחת על המשבצת "לך לכלא" או קיבל 3 פעמים ברצף "דאבל" בהטלות של הקוביה. השחקן נמצא בכלא למשך 3 תורים שבמהלכם יכול לנסות לצאת מהכלא בדרכים הבאים:
    • להשתמש בקלף יציאה מהכלא (שמקבלים מתיבת ההפתעה).
    • לשלם קנס של 50 שקלים.
    • להטיל את הקוביות ולקבל "דאבל".
אם עברו 3 תורים והשחקן לא הצליח לצאת מהכלא, עליו לשלם מס של 50 שקלים ואז הוא יוצא מהכלא.
מהלך המשחק
כל שחקן מתחיל את המשחק עם 1500 שקלים ובתורו מטיל 2 קוביות ומתקדם על הלוח לפי תוצאת ההטלה ולפי החוקים הבאים:
    • אם השחקן נחת ברחוב פנוי, הוא יכול לרכוש את אותו הרחוב.
    • אם השחקן עבר את משבצת ההתחלה, הוא מקבל 200 שקלים לחשבון שלו.
    • אם השחקן נחת במשבצת מיוחדת הוא פועל לפי החוקים של אותה המשבצת (למשל אם נחת במשבצת של תשלום מס השחקן צריך לשלם מס מהחשבון).
    • אם תוצאת ההטלה היא "דאבל" השחקן מקבל תור נוסף למשחק. אם הוא קיבל 3 פעמים ברציפות "דאבל" הוא נכנס לכלא לפי החוקים של "כנס לכלא".
    • אם השחקן נחת בנכס של שחקן אחר עליו לשלם לו שכירות/מס לפי החוקים של המשבצות.
    • אם שחקן לא יכול להרשות לעצמו לשלם מס נוסף הוא "פושט רגל" ויוצא מהמשחק. אם השחקן פושט רגל בגלל חוב לשחקן כלשהו, כל הנכסים של אותו השחקן (כולל הכסף) עוברים לשחקן שהוא הבעלים של החוב. אם החוב הוא לבנק, הבעלות על הרחובות נמחקת.
אם השחקן נחת בכל משבצת שהיא לא "לך לכלא" או "חניה חופשית" השחקן יכול לבנות בתים בנכסים שלו לפי חוקי המשחק.
ניצחון במשחק
שחקן יכול לנצח במשחק רק אם אחד משני הדברים קורים:
    • כל שאר השחקנים פשטו את הרגל.
    • בבעלות השחקן 4000 שקלים.
