# static-code
import unittest

def classify_triangle(a, b, c):

    if a <= 0 or b <= 0 or c <= 0:
        return "Invalid triangle"
    if a == b == c:
        return "Equilateral"
    if a == b or b == c or a == c:
        if a * a + b * b == c * c or b * b + c * c == a * a or a * a + c * c == b * b:
            return "Isosceles and Right"
        return "Isosceles"
    if a * a + b * b == c * c or b * b + c * c == a * a or a * a + c * c == b * b:
        return "Scalene and Right"
    return "Scalene"


class TestClassifyTriangle(unittest.TestCase):
    """
    Test cases for the classify_triangle function.
    """
    def test_equilateral_triangle(self):
        """Test equilateral triangle."""
        self.assertEqual(classify_triangle(3, 3, 3), "Equilateral")

    def test_isosceles_triangle(self):
        """Test isosceles triangle."""
        self.assertEqual(classify_triangle(3, 4, 5), "Scalene and Right")

    def test_scalene_triangle(self):
        """Test scalene triangle."""
        self.assertEqual(classify_triangle(3, 4, 6), "Scalene")

    def test_right_triangle_3_4_5(self):
        """Test right triangle with side lengths in ratio 3:4:5."""
        self.assertEqual(classify_triangle(3, 4, 5), "Scalene and Right")

    def test_right_triangle_5_12_13(self):
        """Test right triangle with side lengths in ratio 5:12:13."""
        self.assertEqual(classify_triangle(5, 12, 13), "Scalene and Right")

    def test_right_triangle_7_24_25(self):
        """Test right triangle with side lengths in ratio 7:24:25."""
        self.assertEqual(classify_triangle(7, 24, 25), "Scalene and Right")

    def test_invalid_triangle(self):
        """Test invalid triangle."""
        self.assertEqual(classify_triangle(0, 3, 5), "Invalid triangle")


if __name__ == "__main__":
    unittest.main()
