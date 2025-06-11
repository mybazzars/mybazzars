@mybazzars.com
// Flutter example for Firebase authentication
Future<User?> signInWithEmail(String email, String password) async {
  try {
    UserCredential result = await FirebaseAuth.instance.signInWithEmailAndPassword(
      email: email,
      password: password,
    );
    return result.user;
  } catch (e) {
    print(e.toString());
    return null;
  }
}// Flutter video upload example
Future<String> uploadVideo(File videoFile) async {
  String fileName = DateTime.now().millisecondsSinceEpoch.toString();
  Reference storageRef = FirebaseStorage.instance.ref().child('videos/$fileName.mp4');
  UploadTask uploadTask = storageRef.putFile(videoFile);
  TaskSnapshot snapshot = await uploadTask;
  return await snapshot.ref.getDownloadURL();
}
// Flutter Stripe payment example
Future<void> makePayment(double amount, String currency) async {
  PaymentIntent intent = await Stripe.instance.createPaymentIntent(
    amount: (amount * 100).toInt(), // in cents
    currency: currency,
  );
  await Stripe.instance.initPaymentSheet(
    paymentSheetParameters: SetupPaymentSheetParameters(
      paymentIntentClientSecret: intent.clientSecret,
      merchantDisplayName: 'YourAppName',
    ),
  );
  await Stripe.instance.presentPaymentSheet();
}
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^2.0.0
  firebase_auth: ^4.0.0
  cloud_firestore: ^4.0.0
  firebase_storage: ^11.0.0
  video_player: ^2.4.0
  stripe_sdk: ^4.0.0
