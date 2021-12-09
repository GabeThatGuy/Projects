```c#
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
/*
 * Written By: Gabriel Gonsalves
 * Written For: Mr. Kolch
 * Date: 2020-02-19
 * Course Code: TER3M1
 * Description: An Ohms law calculator with wattage calculation and memory.
 */

/*
 * Note: All statements and actions in this program contain a try and catch method
 * This is for error handling and is not to be modified.
 * Try: Attempts the code in the brackets
 * Catch: If the code within the try method fails, this code will be executed
 * MessageBox.Show: Shows a messagebox with the contained parameters.
 * Format: MessageBox.Show("MessageBox.Content", "MessageBox.Header");
 */

namespace Ohm_s_Law_Calculator___WindowsForms
{
    public partial class Form1 : Form
    {
        public string memory;

        public Form1()
        {
            InitializeComponent();

        

        }

        private void label1_Click(object sender, EventArgs e)
        {
            
        }
   
        private void ggRSWVoltageSelector_CheckedChanged(object sender, EventArgs e)
        {
            try
            {
                //Reset the Text Fields for disabling
                ggTxtDataInVolts.Enabled = true;
                ggTxtDataInAmps.Enabled = true;
                ggTxtDataInOhms.Enabled = true;



                //Disable the Voltage Text Field in preparation for calculation
                ggTxtDataInVolts.Enabled = false;

                //Reset the Data from any previous calculations
                ggTxtDataInVolts.Text = " ";
                ggTxtDataInAmps.Text = " ";
                ggTxtDataInOhms.Text = " ";
                ggDataOutLblWatts.Text = " ";

                //Reset any data stored in memory
                memory = "";

                //Reset any data stored in the data label.
                ggDataOutTxtLblMem.Text = "";
            } catch(Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
           
        }

        private void ggRSWCurrentSelector_CheckedChanged(object sender, EventArgs e)
        {
            try
            {
                //Reset the Text Fields for disabling
                ggTxtDataInVolts.Enabled = true;
                ggTxtDataInAmps.Enabled = true;
                ggTxtDataInOhms.Enabled = true;

                //Disable the Current Text Field in preparation for calculation
                ggTxtDataInAmps.Enabled = false;

                //Reset the Data from any previous calculations
                ggTxtDataInVolts.Text = " ";
                ggTxtDataInAmps.Text = " ";
                ggTxtDataInOhms.Text = " ";
                ggDataOutLblWatts.Text = " ";

                //Reset any data stored in memory
                memory = "";

                //Reset any data stored in the data label.
                ggDataOutTxtLblMem.Text = "";
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }

        }
     

        private void ggRSWResistanceSelector_CheckedChanged(object sender, EventArgs e)
        {
            try
            {
                //Reset the Text Fields for disabling
                ggTxtDataInVolts.Enabled = true;
                ggTxtDataInAmps.Enabled = true;
                ggTxtDataInOhms.Enabled = true;

                //Disable the Resistance Text Field in preparation for calculation
                ggTxtDataInOhms.Enabled = false;

                //Reset the Data from any previous calculations
                ggTxtDataInVolts.Text = " ";
                ggTxtDataInAmps.Text = " ";
                ggTxtDataInOhms.Text = " ";
                ggDataOutLblWatts.Text = " ";

                //Reset any data stored in memory
                memory = "";

                //Reset any data stored in the data label.
                ggDataOutTxtLblMem.Text = "";
            }

            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggCmdBtnCalcVolts_Click(object sender, EventArgs e)
        {
            try
            {
                //Assign each piece of data to a variable.
                double volts;
                double amps = Convert.ToDouble(ggTxtDataInAmps.Text);
                double ohms = Convert.ToDouble(ggTxtDataInOhms.Text);

                //Calculate the required data
                volts = amps * ohms;
                double watts = volts * amps;

                //Output the data to the corresponding labels
                ggTxtDataInVolts.Text = Convert.ToString(volts);
                ggDataOutLblWatts.Text = ((Convert.ToString(watts)) + " or " + (watts / 1000) + " kW");
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }

        }

        private void ggBtnCmdCalcAmps_Click(object sender, EventArgs e)
        {
            try
            {
                //Assign each piece of data to a variable.
                double volts = Convert.ToDouble(ggTxtDataInVolts.Text);
                double amps;
                double ohms = Convert.ToDouble(ggTxtDataInOhms.Text);

                //Calculate the required data
                amps = volts / ohms;
                double watts = volts * amps;

                //Output the data to the corresponding labels
                ggTxtDataInAmps.Text = Convert.ToString(amps);
                ggDataOutLblWatts.Text = ((Convert.ToString(watts)) + " or " + (watts / 1000) + " kW");
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggBtnCmdCalcOhms_Click(object sender, EventArgs e)
        {
            try
            {
                //Assign each piece of data to a variable.
                double volts = Convert.ToDouble(ggTxtDataInVolts.Text);
                double amps = Convert.ToDouble(ggTxtDataInAmps.Text);
                double ohms;

                //Calculate the required data
                ohms = volts / amps;
                double watts = volts * amps;

                //Output the data to the corresponding labels
                ggTxtDataInOhms.Text = Convert.ToString(ohms);
                ggDataOutLblWatts.Text = ((Convert.ToString(watts)) + " or " + (watts / 1000) + " kW");
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggBtnCmdExit_Click(object sender, EventArgs e)
        {
            //Code for the button to exit the program
            this.Close();
        }

        private void ggBtnCmdVoltsMemRCL_Click(object sender, EventArgs e)
        {
            try
            {
                //Recall the data from memory and store it in the text box.
                ggTxtDataInVolts.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggBtnCmdAmpsMemRCL_Click(object sender, EventArgs e)
        {
            try
            {
                //Recall the data from memory and store it in the text box.
                ggTxtDataInAmps.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggBtnCmdOhmsMemRCL_Click(object sender, EventArgs e)
        {
            try
            {  //Recall the data from memory and store it in the text box.
                ggTxtDataInOhms.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }
        }

        private void ggBtnCmdVoltsMemSTO_Click(object sender, EventArgs e)
        {
            try
            {//Assign a variable for the previous data shown in memory
                String oldmem = memory;

                //Get the data from the text box and store it in memory
                memory = ggTxtDataInVolts.Text;

                //Output the data from memory to the label onscreen
                ggDataOutTxtLblMem.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }

        }

        private void ggBtnCmdAmpsMemSTO_Click(object sender, EventArgs e)
        {
            try
            {
                //Assign a variable for the previous data shown in memory
                String oldmem = memory;

                //Get the data from the text box and store it in memory
                memory = ggTxtDataInAmps.Text;

                //Output the data from memory to the label onscreen
                ggDataOutTxtLblMem.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }

        }

        private void ggBtnCmdOhmsMemSTO_Click(object sender, EventArgs e)
        {
            try
            {
                //Assign a variable for the previous data shown in memory
                String oldmem = memory;

                //Get the data from the text box and store it in memory
                memory = ggTxtDataInOhms.Text;

                //Output the data from memory to the label onscreen
                ggDataOutTxtLblMem.Text = memory;
            }
            catch (Exception)
            {
                MessageBox.Show("Sorry! You typed something in the program that caused it to crash. Please double check all data!", "Error");
            }


        }

        private void label2_Click(object sender, EventArgs e)
        {
            //This code section has no action, please ignore.
        }
    }
}

```
[Back](/Projects/gr12compeng)

