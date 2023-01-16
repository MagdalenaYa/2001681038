# 2001681038
HW- Magdalena Yankova
UD- This was one of mynfirst projects as a software delepoer, and now im looking back at it..-

namespace HWCalculator
{
    public partial class Calculator : Form
    {
        private double memory;
        private double result = 0;
       

        public Calculator()
        {
            InitializeComponent();
        }

        private void button7_Click(object sender, EventArgs e)
        {

        }

        private void Calculator_Load(object sender, EventArgs e)
        {
            lblSign.Text = "";
            btnMC.Enabled = false;
            btnMR.Enabled = false;
        }

        private void btnNumbers(object sender, EventArgs e)
        {
            if (tbLast.Text.Contains(result.ToString()))
            {
                tbFirst.Text = "";
                tbLast.Text = "";
                tbSecond.Text = "";
                lblSign.Text = "";
                if (lblSign.Text == "")
                {
                    tbFirst.Text += ((Button)sender).Text;
                }
                else
                {
                    tbSecond.Text += ((Button)sender).Text;
                }

            }
            else
            {
                if (lblSign.Text == "")
                {
                    tbFirst.Text += ((Button)sender).Text;
                }
                else
                {
                    tbSecond.Text += ((Button)sender).Text;
                }
            }



          
           
        }

        private void btnSign(object sender, EventArgs e)
        {
            lblSign.Text = ((Button)sender).Text;
        }

        private void bntRavno_Click(object sender, EventArgs e)
        {
            int number1;
            int number2;
            try
            {
                number1 = int.Parse(tbFirst.Text);
                number2 = int.Parse(tbSecond.Text);
            } catch(FormatException ex )
             {
                tbFirst.Text = "Error";
                tbSecond.Text = "Error";
                tbLast.Text = "Error";

                MessageBox.Show("Invalid Values!");
                return;
            }catch(OverflowException ex)
            {
                tbFirst.Text = "Error";
                tbSecond.Text = "Error";
                tbLast.Text = "Error";
                MessageBox.Show("Number is ToolBar big!");
                return;
            }

            switch (lblSign.Text)
            {

                case "+":

                    result = number1 + number2;
                    break;
                case "-":
                    result = number1 - number2;
                    break;
                case "*":
                    result = number1 * number2;
                    break;
                case "√":
                    result = Math.Pow(number1, number2);
                    break;
                case "/":
                    try
                    {
                        result = number1 / number2;
                    }
                    catch (DivideByZeroException ex)
                    {
                        MessageBox.Show(ex.Message);
                    }
                    break;





                   
                default:
                    MessageBox.Show("Please enter operation!");
                    break;
            }
            tbLast.Text = result.ToString();
            
               


        }

        private void btnClear_Click(object sender, EventArgs e)
        {
            lblSign.Text = "";
            tbFirst.Text = "";
            tbLast.Text = "";
            tbSecond.Text = "";
        }

        private void btnKoren_Click(object sender, EventArgs e)
        {
            lblSign.Text = "√";
        }

        private void btnMR_Click(object sender, EventArgs e)
        {
            tbLast.Text = memory.ToString();
        }

        private void btnMC_Click(object sender, EventArgs e)
        {
            tbLast.Text = "";
            memory = 0;
            btnMR.Enabled = false;
            btnMC.Enabled = false;
        }

        private void btnMPlus_Click(object sender, EventArgs e)
        {
            lblSign.Text = "+";
           
           
                if (((Button)sender).Text.Contains ("M+"))
                {
                return;
                }
                else if (((Button)sender).Text.Contains("M-"))
                {
                return;
            }
            else
            {
                tbSecond.Text += ((Button)sender).Text;

                memory += double.Parse(tbSecond.Text);
            }
               



        }

        private void bntMMinus_Click(object sender, EventArgs e)
        {
            lblSign.Text = "-";
            if (((Button)sender).Text.Contains("M+"))
            {
                return;
            }
            else if (((Button)sender).Text.Contains("M-"))
            {
                return;
            }
            else
            {
                tbSecond.Text += ((Button)sender).Text;
                memory -= double.Parse(tbSecond.Text);
            }
               

           
        }

        private void btnMS_Click(object sender, EventArgs e)
        {
            memory += double.Parse(tbLast.Text);
            btnMR.Enabled = true;
            btnMC.Enabled = true;
          
        }

       
    }
}
