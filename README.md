# Android_Review_8
Intent to Activity or Context 意圖分享純文本


1. design layout with UI element. And add on Guideline to make a space between ImageView & ImageButton.

       //activity_main.xml
       
       <?xml encoding="utf-8"?>
       
       <layout>
       
           <data>
           
               <variable
                  name="price"
                  type="Integer"
               />
               
               <variable
                   name="volume"
                   type="Integer"
               />
               
           </data>
           
           <androidx.constraintlayout.widget.ConstraintLayout
              tools:context=".MainActivity"
           >
           
           <ImageView
             android:id="img"
             android:scaleType="centerCrop"
             android:srcCompat="@drawable/aaa"
           />
           
           <androidx.constraintlayout.widget.Guideline
              android:id="@+id/ggg"
              android:orientation=""
              app:layout_constaintGuide_end="@dimen/default_spacing"
           />
           
           <TextView
              android:id="@+id/price"
           />
           
           <TextView
              android:id="@+id/volume"
           />
           
           <ImageButton
              android:id="imgB"
              android:scaleType="centerCrop"
              tools:src="@drawable/bbb"
           />
           
           </androidx.constraintlayout.widget.ConstraintLayout>
       
       </layout>
       
2. define dimens.

          // go to app/src/main/res/values/dimens.xml
          
          <?xml encoding="utf-8"?>
          
          <resources>
              <dimen name="default_spacing"> 16dp </dimen>
          </resources>

3. define customed color.

           // go to app/src/main/res/values/colors.xml
           
           <?xml encoding="utf-8"?>
           
           <resources>
           
              <color name="white">#ffffff</color>
              <color name="green">#6ab343</color>
              <color name="grey">#99000000</color>
              
           </resources>

4. define resorces in app/src/main/res/drawable.

5. design menu resource.

       // go to app/src/main/res/menu
       // main_menu.xml
       
       <?xml encoding="utf-8">
       <menu>
          <item
              android:id="@+id/showMenuTouch"
              android:icon="?android:attr/actionModeShareDrawable"
              android:visible="true"
              andrdoid:enable="true"
              android:showAsAction="ifRoom"
          />
       </menu>
       
6. to create a R.string which is located in file called string.xml under dir res/values/.

       <resources>
           <string name="app_name">Dessert Clicker</string>
           <string name="dollar_sign">$</string>
           <string name="zero">0</string>
           <string name="dessert_sold">Desserts Sold</string>
           <string name="share_text">I\'ve clicked %1$d Desserts for a total of %2$d$ #AndroidDessertClicker</string>
           <string name="share">Share</string>
           <string name="sharing_not_available">Sharing Not Available</string>
       </resources>

7. source line of code.

       package com.example.android.katesapp
       
       [default module]
       import android.os.bundle
       import androidx.appcompat.app.AppCompatActivity
       
       [databind module]
       import androidx.databinding.DataBindingUtil
       import com.example.android.katesapp.databinding.ActivityMainBinding
       
       [intent module]
       import androidx.core.app.ShareCompat
       
       [system error handler module]
       import android.content.ActivityNotFoundException
       
       [menu module]
       import android.view.Menu
       import android.view.MenuItem
       
       [Toast module]
       import android.widget.Toast
       
       class MainActivity: AppCompatActivity(){
       
          
            // 類別中的共用變數
            private var price = 0
            private var volume = 0
            private lateinit var binding: ActivityMainBinding
            
            
            // 製作資料型別
            data class garminWatchToBuy(val)
            
            // create a Data Type
            // Data Class
            // it includes the resource id.
            data class garmin3C(val imgId: Int, val price: Int, val volumn: Int)
            
            // 建立集合裝載資料型別的成員
            // create a List
            // 拆解集合為成員
            private val allGarmin3C = listOf(
            
               garmin3C(R.drawable.watchA, 6990, 5),
               garmin3C(R.drawable.watchB, 7990, 15),
               garmin3C(R.drawable.watchC, 19900, 20)
            
            
            )
            
            
            // 提取集合中的成員，成員有 id、價格、數量等屬性
            private var currentWatch = allGarmin[0]
       
            override fun onCreate(savedInstanceState: Bundle?){
            
                 super.onCreate(savedInstanceState)
                 
                 // 綁定 UI 元件
                 binding = DataBindingUtil.setContentView(this, R.layout.activity_main)
                 
                 // 顯示 UI 元件
                 binding.imgB.setOnClickListner {
                     clickBuyHandler()
                 }
                 
                 binding.imgB.setImageResource(currentWatch.imgId)
                 
                 binding.price = price
                 binding.volumn = volumn
           
                 
            }
            
            private fun clickBuyHandler() {
               
               // update value of volumn when user click on the button to demonstrate he/she wanna buy it
               volumnAfterBuy--
               
               binding.volumn = volumnAfterBuy
               
               showOtherWatch()
            
            
            }
            
            private fun showOtherWatch() {
            
                 // TODO
                 // for-in loop
                 // use the data class called allGraminWatch 
            
            
            } 
            
            // Menu to be inflated
            override fun onCreateOptionsMenu(menu: Menu): Boolean {
            
               menuInflater.inflate(R.menu.main_menu, menu)
               return super.onCreateOptionsMenu(menu)
               
            }
            
            // Items to be selected
            override fun onOptionsItemSelected(item: MenuItem): Boolean {
            
               // lambda
               // (itemId) -> {body}
               // {itemId -> body}
               when(item.itemId){
                   R,id.showMenuTouch -> showGarmin()
               }
               return super.onOptionsItemSelected(item)
            
            }
            
            // ShareCompat is a public class
            // its IntentBuilder is a constructor
            // then call its methods and properties
            // Intent 
            // Exception Handler
            private fun showGarmin() {
            
                 // Intent
                 // setText(CharSequence text) 
                 // Set the literal text data to be sent as part of the share.
                 // Question on R.string.share_text
                 val showIntent = ShareCompat.IntentBuilder.from(this).setText(getString(R.string.share_text, price, volumn)).setType("text/plain").intent
                 
                 try {
                 
                     startActivity(showIntent)
                 
                 } catch(ex: ActivityNotFoundException) {
                 
                     Toast.makeText(this, getString(), Toast.LENGTH_LONG).show()
                 
                 }
            
            }
                   
       
       }


8. today's tip (getString())

   https://cloud.tencent.com/developer/ask/72642
