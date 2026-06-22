# BÀI 1: Phân tích & Lựa chọn  
## Kỹ thuật Prompt suy luận theo các bước - Chain-of-thought

---

## 1. Đáp án lựa chọn

**Đáp án đúng: Phương án B**

Phương án B là prompt tối ưu nhất vì nó hướng dẫn AI phân tích bài toán theo từng bước rõ ràng trước khi sinh mã nguồn. Đối với bài toán tính thuế thu nhập cá nhân lũy tiến, nếu chỉ yêu cầu AI viết code ngay thì rất dễ xảy ra lỗi ở các ranh giới bậc thuế, lỗi làm tròn số tiền hoặc tính sai phần thu nhập chịu thuế. Vì vậy, prompt cần yêu cầu AI phân tích công thức, xác định dữ liệu đầu vào, chạy thử bằng tay và sau đó mới viết code.

---

## 2. Phân tích tại sao phương án B tối ưu nhất

Phương án B có nội dung:

> Hãy đóng vai trò là một Java Developer chuyên nghiệp kiêm chuyên gia tài chính. Nhiệm vụ của bạn là viết một class Java tính thuế thu nhập cá nhân lũy tiến dựa trên thu nhập chịu thuế. Ràng buộc: Sử dụng Java 17, kiểu dữ liệu BigDecimal để tránh sai số làm tròn tiền tệ. Các bậc thuế lũy tiến giả định...

Đây là phương án tốt nhất vì đáp ứng đầy đủ các nguyên tắc của kỹ thuật Chain-of-thought và cấu trúc 5 thành phần của một prompt hiệu quả.

### 2.1. Có vai trò rõ ràng

Prompt yêu cầu AI đóng vai:

**“Java Developer chuyên nghiệp kiêm chuyên gia tài chính”**

Điều này giúp AI hiểu rằng bài toán không chỉ là viết code Java thông thường, mà còn liên quan đến nghiệp vụ tài chính, tiền tệ và thuế thu nhập cá nhân. Khi có vai trò rõ ràng, AI sẽ có xu hướng xử lý bài toán cẩn thận hơn.

---

### 2.2. Có nhiệm vụ cụ thể

Prompt nêu rõ nhiệm vụ:

**“Viết một class Java tính thuế thu nhập cá nhân lũy tiến dựa trên thu nhập chịu thuế.”**

Nhiệm vụ này rõ ràng hơn rất nhiều so với việc chỉ nói chung chung là “viết hàm tính thuế”. AI biết cần tạo class, dùng Java và tập trung vào thuật toán tính thuế lũy tiến.

---

### 2.3. Có bối cảnh nghiệp vụ đầy đủ

Phương án B cung cấp đầy đủ các yếu tố nghiệp vụ quan trọng:

- Giảm trừ bản thân: **11.000.000 VND**
- Giảm trừ người phụ thuộc: **4.400.000 VND/người**
- Bảo hiểm bắt buộc: **10,5% tổng thu nhập**
- Biểu thuế lũy tiến từng phần gồm 7 bậc

Đây là thông tin bắt buộc để AI tính đúng thu nhập tính thuế và tiền thuế phải nộp.

---

### 2.4. Có ràng buộc kỹ thuật rõ ràng

Prompt yêu cầu:

- Sử dụng **Java 17**
- Sử dụng **BigDecimal** để tránh sai số tiền tệ

Đây là điểm rất quan trọng. Trong Java, nếu dùng `double` hoặc `float` để tính tiền thì có thể phát sinh sai số do cách biểu diễn số thực nhị phân. Với bài toán tài chính, `BigDecimal` là lựa chọn phù hợp hơn vì kiểm soát được độ chính xác và cách làm tròn.

---

### 2.5. Có quy trình Chain-of-thought rõ ràng

Phương án B yêu cầu AI không viết code ngay mà phải làm theo từng bước:

1. Phân tích cách xác định thu nhập tính thuế.
2. Liệt kê công thức tính thuế cho từng bậc.
3. Dry-run bằng ví dụ cụ thể.
4. Cuối cùng mới sinh mã nguồn Java hoàn chỉnh.

Đây chính là tinh thần của kỹ thuật Chain-of-thought: yêu cầu AI suy luận từng bước để giảm lỗi logic. Với bài toán tính thuế lũy tiến, việc phân tích từng bước giúp kiểm soát tốt các vấn đề như:

- Thu nhập âm hoặc bằng 0 thì không phải nộp thuế.
- Chỉ phần thu nhập nằm trong từng bậc mới bị đánh thuế theo tỷ lệ của bậc đó.
- Không tính toàn bộ thu nhập theo một mức thuế duy nhất.
- Không tính sai phần chênh lệch giữa các ngưỡng thuế.
- Không dùng kiểu dữ liệu gây sai số tiền tệ.

---

## 3. Phân tích theo cấu trúc 5 thành phần của Prompt

Một prompt hiệu quả thường có 5 thành phần chính: vai trò, nhiệm vụ, bối cảnh, ràng buộc và định dạng đầu ra.

| Thành phần | Phương án B thể hiện như thế nào? |
|---|---|
| Vai trò | Java Developer chuyên nghiệp kiêm chuyên gia tài chính |
| Nhiệm vụ | Viết class Java tính thuế TNCN lũy tiến |
| Bối cảnh | Tính thu nhập chịu thuế sau giảm trừ và áp dụng biểu thuế lũy tiến |
| Ràng buộc | Java 17, BigDecimal, các bậc thuế cụ thể, tránh sai số làm tròn |
| Định dạng đầu ra | Phân tích từng bước, dry-run, sau đó sinh mã nguồn Java hoàn chỉnh |

Nhờ có đủ 5 thành phần này, phương án B giúp AI hiểu rõ cần làm gì, làm theo quy trình nào và tạo ra kết quả ở dạng nào.

---

## 4. Lý do loại trừ các phương án còn lại

### 4.1. Loại phương án A

Phương án A:

> “Hãy viết hàm Java tính thuế thu nhập cá nhân lũy tiến theo biểu thuế Việt Nam hiện hành. Hãy tối ưu nhất.”

Phương án này có một số nhược điểm:

- Quá ngắn và thiếu bối cảnh chi tiết.
- Không nêu rõ mức giảm trừ bản thân, người phụ thuộc và bảo hiểm.
- Không yêu cầu sử dụng `BigDecimal`, dễ khiến AI dùng `double` hoặc `float`.
- Không cung cấp bảng thuế cụ thể, có thể khiến AI dùng sai biểu thuế.
- Cụm từ **“tối ưu nhất”** mơ hồ, không nói rõ tối ưu về hiệu năng, độ chính xác hay cấu trúc code.
- Không yêu cầu AI phân tích từng bước trước khi viết code.

Do đó, phương án A có nguy cơ tạo ra code thiếu chính xác, đặc biệt ở các ranh giới bậc thuế.

---

### 4.2. Loại phương án C

Phương án C:

> “Hãy đóng vai trò Senior Developer. Hãy viết một class Java tính thuế TNCN lũy tiến sử dụng Java Stream API song song để tính toán cực nhanh các bậc thuế lũy tiến nhằm tối ưu hiệu năng.”

Phương án này có vai trò rõ hơn phương án A, nhưng vẫn không phù hợp vì:

- Tập trung sai trọng tâm vào hiệu năng thay vì độ chính xác.
- Tính thuế lũy tiến là bài toán có rất ít bậc thuế, chỉ 7 bậc, nên không cần dùng parallel stream.
- Sử dụng Stream API song song có thể làm code phức tạp hơn, khó đọc hơn và dễ sai logic hơn.
- Không nhắc đến `BigDecimal`, dễ gây sai số tiền tệ.
- Không yêu cầu phân tích từng bước.
- Không yêu cầu dry-run để kiểm tra kết quả.
- Không nêu rõ các khoản giảm trừ và bảng thuế.

Với bài toán tài chính, tiêu chí quan trọng nhất là **đúng nghiệp vụ, đúng ranh giới, đúng số tiền**, không phải chạy nhanh bằng mọi giá. Vì vậy, phương án C không phải lựa chọn tối ưu.

---

## 5. Dry-run ví dụ theo phương án B

Ví dụ:

- Tổng thu nhập: **30.000.000 VND**
- Số người phụ thuộc: **1**
- Không tính bảo hiểm

### Bước 1: Tính các khoản giảm trừ

Giảm trừ bản thân:

```text
11.000.000 VND
```

Giảm trừ người phụ thuộc:

```text
1 x 4.400.000 = 4.400.000 VND
```

Bảo hiểm:

```text
0 VND
```

Tổng giảm trừ:

```text
11.000.000 + 4.400.000 + 0 = 15.400.000 VND
```

### Bước 2: Tính thu nhập tính thuế

```text
Thu nhập tính thuế = 30.000.000 - 15.400.000 = 14.600.000 VND
```

### Bước 3: Tính thuế lũy tiến từng phần

Thu nhập tính thuế là **14.600.000 VND**, thuộc đến bậc 3.

- Bậc 1: 5.000.000 x 5% = 250.000 VND
- Bậc 2: 5.000.000 x 10% = 500.000 VND
- Bậc 3: 4.600.000 x 15% = 690.000 VND

Tổng thuế phải nộp:

```text
250.000 + 500.000 + 690.000 = 1.440.000 VND
```

---

## 6. Mã nguồn Java hoàn chỉnh

```java
import java.math.BigDecimal;
import java.math.RoundingMode;
import java.util.Objects;

public class PersonalIncomeTaxCalculator {

    private static final BigDecimal PERSONAL_DEDUCTION = new BigDecimal("11000000");
    private static final BigDecimal DEPENDENT_DEDUCTION = new BigDecimal("4400000");
    private static final BigDecimal DEFAULT_INSURANCE_RATE = new BigDecimal("0.105");

    private static final TaxBracket[] TAX_BRACKETS = {
            new TaxBracket(new BigDecimal("5000000"), new BigDecimal("0.05")),
            new TaxBracket(new BigDecimal("10000000"), new BigDecimal("0.10")),
            new TaxBracket(new BigDecimal("18000000"), new BigDecimal("0.15")),
            new TaxBracket(new BigDecimal("32000000"), new BigDecimal("0.20")),
            new TaxBracket(new BigDecimal("52000000"), new BigDecimal("0.25")),
            new TaxBracket(new BigDecimal("80000000"), new BigDecimal("0.30")),
            new TaxBracket(null, new BigDecimal("0.35"))
    };

    public BigDecimal calculateTax(BigDecimal grossIncome, int numberOfDependents, boolean applyInsurance) {
        validateInput(grossIncome, numberOfDependents);

        BigDecimal taxableIncome = calculateTaxableIncome(grossIncome, numberOfDependents, applyInsurance);

        if (taxableIncome.compareTo(BigDecimal.ZERO) <= 0) {
            return BigDecimal.ZERO.setScale(0, RoundingMode.HALF_UP);
        }

        return calculateProgressiveTax(taxableIncome).setScale(0, RoundingMode.HALF_UP);
    }

    public BigDecimal calculateTaxableIncome(BigDecimal grossIncome, int numberOfDependents, boolean applyInsurance) {
        validateInput(grossIncome, numberOfDependents);

        BigDecimal dependentDeduction = DEPENDENT_DEDUCTION.multiply(BigDecimal.valueOf(numberOfDependents));
        BigDecimal insuranceDeduction = applyInsurance
                ? grossIncome.multiply(DEFAULT_INSURANCE_RATE)
                : BigDecimal.ZERO;

        BigDecimal taxableIncome = grossIncome
                .subtract(PERSONAL_DEDUCTION)
                .subtract(dependentDeduction)
                .subtract(insuranceDeduction);

        return taxableIncome.max(BigDecimal.ZERO).setScale(0, RoundingMode.HALF_UP);
    }

    private BigDecimal calculateProgressiveTax(BigDecimal taxableIncome) {
        BigDecimal totalTax = BigDecimal.ZERO;
        BigDecimal previousLimit = BigDecimal.ZERO;

        for (TaxBracket bracket : TAX_BRACKETS) {
            BigDecimal upperLimit = bracket.upperLimit();
            BigDecimal rate = bracket.rate();

            BigDecimal taxableAmountInBracket;

            if (upperLimit == null) {
                taxableAmountInBracket = taxableIncome.subtract(previousLimit);
            } else {
                taxableAmountInBracket = taxableIncome.min(upperLimit).subtract(previousLimit);
            }

            if (taxableAmountInBracket.compareTo(BigDecimal.ZERO) > 0) {
                BigDecimal taxForBracket = taxableAmountInBracket.multiply(rate);
                totalTax = totalTax.add(taxForBracket);
            }

            if (upperLimit == null || taxableIncome.compareTo(upperLimit) <= 0) {
                break;
            }

            previousLimit = upperLimit;
        }

        return totalTax;
    }

    private void validateInput(BigDecimal grossIncome, int numberOfDependents) {
        Objects.requireNonNull(grossIncome, "Gross income must not be null");

        if (grossIncome.compareTo(BigDecimal.ZERO) < 0) {
            throw new IllegalArgumentException("Gross income must not be negative");
        }

        if (numberOfDependents < 0) {
            throw new IllegalArgumentException("Number of dependents must not be negative");
        }
    }

    private record TaxBracket(BigDecimal upperLimit, BigDecimal rate) {
    }

    public static void main(String[] args) {
        PersonalIncomeTaxCalculator calculator = new PersonalIncomeTaxCalculator();

        BigDecimal grossIncome = new BigDecimal("30000000");
        int numberOfDependents = 1;
        boolean applyInsurance = false;

        BigDecimal taxableIncome = calculator.calculateTaxableIncome(
                grossIncome,
                numberOfDependents,
                applyInsurance
        );

        BigDecimal tax = calculator.calculateTax(
                grossIncome,
                numberOfDependents,
                applyInsurance
        );

        System.out.println("Thu nhập tính thuế: " + taxableIncome + " VND");
        System.out.println("Thuế TNCN phải nộp: " + tax + " VND");
    }
}
```

---

## 7. Kết luận

Phương án B là lựa chọn tối ưu nhất vì nó đầy đủ vai trò, nhiệm vụ, bối cảnh, ràng buộc kỹ thuật và định dạng đầu ra. Đặc biệt, phương án này áp dụng kỹ thuật Chain-of-thought bằng cách yêu cầu AI phân tích từng bước trước khi viết code. Điều này rất phù hợp với bài toán tính thuế TNCN lũy tiến, vì đây là bài toán dễ sai ở công thức, ranh giới bậc thuế và làm tròn số tiền.

Phương án A quá chung chung, thiếu ràng buộc và dễ sinh code sai. Phương án C lại tập trung sai vào hiệu năng, trong khi bài toán tài chính cần ưu tiên độ chính xác và tính rõ ràng của thuật toán.
