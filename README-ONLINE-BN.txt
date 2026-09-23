SRB-8 Online Version

1) Firebase Authentication-এ Google provider Enable করুন।
2) Authentication > Settings > Authorized domains-এ আপনার localhost/GitHub Pages domain যোগ করুন।
3) Firestore Database তৈরি করুন এবং firestore.rules প্রকাশ করুন।
4) Admin Panel-এ শুধু masumbillah6778@gmail.com ও rationrab8@gmail.com অনুমোদিত।
5) Google Account নির্বাচন করার পর Personal App Password দিতে হবে।
6) ডাটা Firestore-এর records/deletedRecords/rationLogs collection-এ থাকবে।
7) দুই ডিভাইস থেকে একই/আলাদা অনুমোদিত Gmail দিয়ে আলাদা session চালানো যাবে।
8) firebase-config.js-এ Firebase Web config রাখা হয়েছে।

গুরুত্বপূর্ণ: বর্তমান User Panel-এ আলাদা Login UI নেই, তাই তার বিদ্যমান আচরণ অক্ষুণ্ণ রাখতে records collection-এর read উন্মুক্ত রাখা হয়েছে; Admin ছাড়া অন্য কেউ records লিখতে পারবে না। ব্যক্তিগত/সংবেদনশীল তথ্য পুরোপুরি private করতে চাইলে User Panel-এর জন্য আলাদা authentication flow প্রয়োজন হবে।

--- SRB-8 User Gmail Login / Active Member Update ---
- User Panel now requires Google/Gmail selection and login before viewing the panel.
- User Panel has no Logout control.
- The currently signed-in Gmail is shown at the bottom of the User Panel sidebar.
- Each successful User Gmail login is registered in Firestore collection: activeMembers.
- Admin Dashboard now has a final yellow card named "এক্টিভ সদস্য" showing the total number of unique Gmail accounts that have logged in.
- Firestore Rules allow an authenticated user to create/update only their own activeMembers document; only approved Admin Gmail accounts can read that collection.
- Deploy firestore.rules to Firebase before testing the new User login/Active Member count.
