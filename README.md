public class OrangeHRMAutomation {
    public static void main(String[] args) throws InterruptedException {
        
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver"); // Update this path
        WebDriver driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
        driver.manage().window().maximize();
        driver.get("https://opensource-demo.orangehrmlive.com/web/index.php/auth/login");
        driver.findElement(By.name("username")).sendKeys("Admin");
        driver.findElement(By.name("password")).sendKeys("admin123");
        driver.findElement(By.xpath("//button[@type='submit']")).click();
        driver.findElement(By.xpath("//span[text()='PIM']")).click();
        driver.findElement(By.xpath("//a[text()='Add Employee']")).click();
        driver.findElement(By.name("firstName")).sendKeys("John");
        driver.findElement(By.name("lastName")).sendKeys("Doe");
        driver.findElement(By.xpath("//button[@type='submit']")).click();
        Thread.sleep(2000);
        driver.findElement(By.xpath("//span[text()='PIM']")).click();
        Thread.sleep(1000);
        driver.findElement(By.xpath("//a[text()='Add Employee']")).click();
        driver.findElement(By.name("firstName")).sendKeys("Jane");
        driver.findElement(By.name("lastName")).sendKeys("Smith");
        driver.findElement(By.xpath("//button[@type='submit']")).click();
        Thread.sleep(2000);
        driver.findElement(By.xpath("//span[text()='PIM']")).click();
        Thread.sleep(1000);
        driver.findElement(By.xpath("//label[text()='Employee Name']/../following-sibling::div//input")).sendKeys("John Doe");
        Thread.sleep(1000); // wait for dropdown
        driver.findElement(By.xpath("//div[@role='option']")).click();
        driver.findElement(By.xpath("//button[@type='submit']")).click();
        Thread.sleep(2000);
        boolean johnExists = driver.getPageSource().contains("John Doe");
        driver.navigate().refresh();
        Thread.sleep(2000);
        driver.findElement(By.xpath("//label[text()='Employee Name']/../following-sibling::div//input")).sendKeys("Jane Smith");
        Thread.sleep(1000);
        driver.findElement(By.xpath("//div[@role='option']")).click();
        driver.findElement(By.xpath("//button[@type='submit']")).click();
        Thread.sleep(2000);
        boolean janeExists = driver.getPageSource().contains("Jane Smith");
        System.out.println("John Doe present: " + johnExists);
        System.out.println("Jane Smith present: " + janeExists);
        driver.findElement(By.xpath("//span[@class='oxd-userdropdown-tab']")).click();
        Thread.sleep(1000);
        driver.findElement(By.xpath("//a[text()='Logout']")).click();
        driver.quit();
    }
}
