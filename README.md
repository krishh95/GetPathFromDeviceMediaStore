public static String getRealPathFromURI(Context context, Uri contentUri) {

   Cursor cursor = null;
   
   try {
   
       String[] proj = {MediaStore.Files.FileColumns.DATA};
       //String[] proj = {MediaStore.Images.Media.DATA};
       cursor = context.getContentResolver().query(contentUri, proj, null, null, null);
       //int column_index = cursor.getColumnIndexOrThrow(MediaStore.Images.Media.DATA);
       int column_index = cursor.getColumnIndexOrThrow(MediaStore.Files.FileColumns.DATA);
       cursor.moveToFirst();
       return cursor.getString(column_index);
   } finally {
       if (cursor != null) {
           cursor.close();
       }
   }
   
}
