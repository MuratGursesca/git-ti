# Cookies

First I Find the total number of cookies.

Second one I Print all the cookies.

Third I get the cookies by their name.

Fourth I add new cookie.

Sixth Delete all cookies.



import deneme.utilities.TestBase;
import org.junit.Test;
import org.openqa.selenium.Cookie;
import org.openqa.selenium.WebElement;

import java.util.Set;

public class Cookies extends TestBase {
    
    @Test
    public void cookieTest(){
        driver.get("https://www.****.com");

//1st Find the total number of cookies

        Set<Cookie> allCookies=driver.manage().getCookies();
        int cookieSize = allCookies.size();
        System.out.println("Original Cookie Size : " +cookieSize);

//2.Print all the cookies

        for (Cookie eachCookie : allCookies){
            System.out.println("Cookie Value : "+eachCookie.getValue());
        }
        for (Cookie eachCookie : allCookies) {
            System.out.println("Cookie Name : " + eachCookie.getName());

        }

//3rd Get the cookies by their name

        System.out.println("COOKIE NAMED : "+driver.manage().getCookieNamed("*****"));

//4th Add new cookie

        Cookie cookie =new Cookie("My-Fav-Cookie", "White-Chocolate");
        driver.manage().addCookie(cookie);
        Set<Cookie> newCookies=driver.manage().getCookies();
        System.out.println("New Cookie Size : "+newCookies.size());

//5th Delete cookie by name

        driver.manage().deleteCookieNamed("i18n-prefs");
        Set<Cookie> newCookies1=driver.manage().getCookies();
        System.out.println("New Cookie Size : "+newCookies1.size());

//6th Delete all cookies

        driver.manage().deleteAllCookies();
        Set<Cookie> newCookies2 = driver.manage().getCookies();
        System.out.println("New Cookie Size : "+newCookies2.size());
    }
}

