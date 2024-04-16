
# Banka ve ATM Simülasyonu

Bu Java programı, bir banka ve ATM sistemi simüle eder. Temel bankacılık işlemlerini gerçekleştirebilir ve kullanıcıların hesaplarını yönetmelerine olanak tanır.

## Özellikler

- Banka hesaplarını oluşturma, kapatma ve işlem yapma.
- Şirket ve müşteri hesaplarını yönetme.
- İşlem geçmişini işleme ve hataları raporlama.
- Hesap bakiyelerini kontrol etme ve güncelleme.

## Nasıl Kullanılır

1. Programı çalıştırarak banka ve ATM sistemini başlatın.
2. Yeni müşteriler ve şirketler ekleyin.
3. Hesapları oluşturun ve işlem yapın.
4. İşlem geçmişini inceleyin ve gerekirse hataları düzeltin.
5. Programı kapatmadan önce güncellemeleri kaydedin.

## Örnek Kod

```java
// Örnek bir işlem yapma
Bank b = new Bank("My Bank", "My Bank's Address");
b.addCompany(1, "Company 1");
b.getCompany(1).openAccount("1234", 0.05);
b.addAccount(b.getCompany(1).getAccount("1234"));
b.getAccount("1234").deposit(500000);
b.getCompany(1).getAccount("1234").deposit(500000);
b.getCompany(1).openAccount("1235", 0.03);
b.addAccount(b.getCompany(1).getAccount("1235"));
b.getCompany(1).getAccount("1235").deposit(25000);
b.addCompany(2, "Company 2");
b.getCompany(2).openAccount("2345", 0.03);
b.addAccount(b.getCompany(2).getAccount("2345"));
b.getCompany(2).getAccount("2345").deposit(350);
b.addCustomer(1, "Customer", "1");
Customer c = b.getCustomer(1);
c.openAccount("3456");
c.openAccount("3457");
c.getAccount("3456").deposit(150);
c.getAccount("3457").deposit(250);
System.out.println(b.toString());

// İşlemleri işleme ve hataları raporlama
Collection<Transaction> transactions = new ArrayList<Transaction>();
transactions.add(new Transaction(3, "4567", 40000)); // Hata
transactions.add(new Transaction(1, "4567", 3100));  // Başarılı
transactions.add(new Transaction(1, "4567", 0));     // Hata
transactions.add(new Transaction(3, "4567", 8000000));// Hata
transactions.add(new Transaction(9, "4567", 80));    // Hata

b.processTransactions(transactions, "Out.txt");
System.out.println(b);
