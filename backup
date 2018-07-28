import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;

///////////////////////////////////////////////////////////////////////////////
//                
// Title:            HW10
// Files:            Neural.java
// Semester:         Fall 2017
//
// Author:           Akshay Mishra, mishra27@wisc.edu
// CS Login:         mishra
// Lecturer's Name:  Jerry
//
//////////////////////////// 80 columns wide //////////////////////////////////

/**
 * We will build a neural network to perform binary classification
 * @author aksha
 *
 */
public class Neural {
	public static void main(String[] args) {

		// initializing flag and weights
		int flag = Integer.valueOf(args[0]);
		double w1 = Double.valueOf(args[1]);
		double w2 = Double.valueOf(args[2]);
		double w3 = Double.valueOf(args[3]);
		double w4 = Double.valueOf(args[4]);
		double w5 = Double.valueOf(args[5]);
		double w6 = Double.valueOf(args[6]);
		double w7 = Double.valueOf(args[7]);
		double w8 = Double.valueOf(args[8]);
		double w9 = Double.valueOf(args[9]);

		
		// if flag is 100 print u and v values
		if (flag == 100) {
			
			// initializing x1 and x2
			double x1 = Double.valueOf(args[10]);
			double x2 = Double.valueOf(args[11]);

			// calculating u_A and v_A
			double uA = w1 + (w2 * x1) + (w3 * x2);
			double vA = max(uA, 0);

			// calculating u_B and v_B
			double uB = w4 + (w5 * x1) + (w6 * x2);
			double vB = max(uB, 0);

			// calculating u_C and v_C
			double uC = w7 + (w8 * vA) + (w9 * vB);
			double vC = 1 / (1 + Math.exp(-uC));

			// printing out calculated values
			System.out.print(String.format("%.5f", uA) + " " + 
					String.format("%.5f", vA) + " ");
			System.out.print(String.format("%.5f", uB) + " " +
					String.format("%.5f", vB) + " ");
			System.out.println(String.format("%.5f", uC) + " " + 
					String.format("%.5f", vC));

		}
		
		// this block when flag is 200 - 500
		if (flag == 200 || flag == 300 || flag == 400 || flag == 500) {

			// initializing variables
			double x1 = Double.valueOf(args[10]);
			double x2 = Double.valueOf(args[11]);
			double y = Double.valueOf(args[12]);

			// calculating u_A and v_A
			double uA = w1 + (w2 * x1) + (w3 * x2);
			double vA = max(uA, 0);
			
			// calculating u_B and v_B
			double uB = w4 + (w5 * x1) + (w6 * x2);
			double vB = max(uB, 0);

			// calculating u_C and v_C
			double uC = w7 + (w8 * vA) + (w9 * vB);
			double vC = 1 / (1 + Math.exp(-uC));
			
			// using v_C and y ti find error
			double e = (0.5) * (vC - y) * (vC - y);

			// The partial derivative with respect to the output layer 
			// variable v_C
			double partialWithVc = vC - y;
			
			// The partial derivative with respect to the intermediate 
			// variable u_C
			double partialWithUc = partialWithVc * vC * (1.0 - vC);

			// The partial derivative with respect to output layer variable
			// V_a, uses partial derivative with respect to U_k from next
			// level (i.e. partialWithUc)
			double partialWithVa = w8 * partialWithUc;
			
			// calculation below for The partial derivative with respect to
			// the intermediate variable u_a
			double partialVaOverPartialUa;

			if (uA >= 0)
				partialVaOverPartialUa = 1;
			else
				partialVaOverPartialUa = 0;

			double partialWithUa = partialWithVa * partialVaOverPartialUa;

			// The partial derivative with respect to output layer variable
			// V_b, uses partial derivative with respect to U_k from next
			// level (i.e. partialWithUc)
			double partialWithVb = w9 * partialWithUc;
			
			// calculation below for The partial derivative with respect to
			// the intermediate variable u_a
			double partialVbOverPartialUb;

			if (uB >= 0)
				partialVbOverPartialUb = 1;
			else
				partialVbOverPartialUb = 0;

			double partialWithUb = partialWithVb * partialVbOverPartialUb;

			// partial derivative with respect to the edge weights			
			double derivativeWithWeight1 = 1 * partialWithUa;
			double derivativeWithWeight2 = x1 * partialWithUa;
			double derivativeWithWeight3 = x2 * partialWithUa;
			double derivativeWithWeight4 = 1 * partialWithUb;
			double derivativeWithWeight5 = x1 * partialWithUb;
			double derivativeWithWeight6 = x2 * partialWithUb;
			double derivativeWithWeight7 = 1 * partialWithUc;
			double derivativeWithWeight8 = vA * partialWithUc;
			double derivativeWithWeight9 = vB * partialWithUc;

			// prints error, partial derivative w.r.t v_C and partial 
			// derivative w.r.t u_C when flag is 200 
			if (flag == 200) {

				System.out.print(String.format("%.5f", e) + " ");
				System.out.print(String.format("%.5f", partialWithVc) + " ");
				System.out.println(String.format("%.5f", partialWithUc));

			}
			
			// prints partial derivative w.r.t v_A, partial derivative w.r.t 
			// u_A and partial derivative w.r.t v_B, partial derivative w.r.t
			// u_B, when flag is 300 
			if (flag == 300) {

				System.out
				.print(String.format("%.5f", partialWithVa) + " " + 
						String.format("%.5f", partialWithUa) + " ");
				System.out.println(String.format("%.5f", partialWithVb) + 
						" " + String.format("%.5f", partialWithUb));

			}

			// prints partial derivative with respect to the edge weights
			// when flag is 400
			if (flag == 400) {
				System.out.print(String.format("%.5f", derivativeWithWeight1) +
					" "	+ String.format("%.5f", derivativeWithWeight2) + " "
						+ String.format("%.5f", derivativeWithWeight3) + " ");
				System.out.print(String.format("%.5f", derivativeWithWeight4) 
					+ " " + String.format("%.5f", derivativeWithWeight5) + " "
						+ String.format("%.5f", derivativeWithWeight6) + " ");
				System.out.println(String.format("%.5f", derivativeWithWeight7) +
						" "	+ String.format("%.5f", derivativeWithWeight8) + 
						" "	+ String.format("%.5f", derivativeWithWeight9));
			}

			// prints old weights, errors, updated weights and new error in
			// 4 separate lines when flag is 500
			if (flag == 500) {

				// initializing step size
				double n = Double.valueOf(args[13]);

				// prints old weights
				System.out.print(String.format("%.5f", w1) + " " + 
						String.format("%.5f", w2) + " "
						+ String.format("%.5f", w3) + " ");
				System.out.print(String.format("%.5f", w4) + " " + 
						String.format("%.5f", w5) + " "
						+ String.format("%.5f", w6) + " ");
				System.out.println(	String.format("%.5f", w7) + " " + 
						String.format("%.5f", w8) + " " + String.format
						("%.5f", w9));
				
				// prints old error
				System.out.println(String.format("%.5f", e));

				// updates weights
				w1 = w1 - (n * derivativeWithWeight1);
				w2 = w2 - (n * derivativeWithWeight2);
				w3 = w3 - (n * derivativeWithWeight3);
				w4 = w4 - (n * derivativeWithWeight4);
				w5 = w5 - (n * derivativeWithWeight5);
				w6 = w6 - (n * derivativeWithWeight6);
				w7 = w7 - (n * derivativeWithWeight7);
				w8 = w8 - (n * derivativeWithWeight8);
				w9 = w9 - (n * derivativeWithWeight9);

				// finds new u and v vales for each node based on new weights
				double newUa = w1 + (w2 * x1) + (w3 * x2);
				double newVa = max(newUa, 0);

				double newUb = w4 + (w5 * x1) + (w6 * x2);
				double newVb = max(newUb, 0);

				double newUc = w7 + (w8 * newVa) + 
						(w9 * newVb);
				double newVc = 1 / (1 + Math.exp(-newUc));
				
				// finds new error
				double error = (0.5) * (newVc - y) * (newVc - y);

				// prints new weights
				System.out.print(String.format("%.5f", w1) + " " +
				String.format("%.5f", w2) + " "
						+ String.format("%.5f", w3) + " ");
				System.out.print(String.format("%.5f", w4) + " " + 
						String.format("%.5f", w5) + " "
						+ String.format("%.5f", w6) + " ");
				System.out.println(String.format("%.5f", w7) + " " +
						String.format("%.5f", w8) + " "
						+ String.format("%.5f", w9));
				
				// prints new error
				System.out.println(String.format("%.5f", error));

			}
		}

		// reads files to train the neural 
		// Run one epoch (i.e. going over the 67 training items once). 
		// For each training item, print three lines:
		//	(a) x1, x2, y
		//	(b) the updated w1 . . . w9
		//	(c) the evaluation set error under the updated w
		if (flag == 600) {

			// initializes step size
			double n = Double.valueOf(args[10]);

			// reads training items from the text file
			try (BufferedReader br = new BufferedReader(new FileReader
					("hw2_midterm_A_train.txt"))) {

				// reads every line till EOF
				for (String line; (line = br.readLine()) != null;) {
					
					double error = 0;
					
					// data array to store data for each students
					String[] data = line.split("\\s+");

					// updates x1, x2 and y
					Double x1 = Double.parseDouble(data[0]);
					Double x2 = Double.parseDouble(data[1]);
					Double y = Double.parseDouble(data[2]);

					
					// finds u and v values based on x1, x2 and y values
					double uA = w1 + (w2 * x1) + (w3 * x2);
					double vA = max(uA, 0);

					double uB = w4 + (w5 * x1) + (w6 * x2);
					double vB = max(uB, 0);

					double uC = w7 + (w8 * vA) + (w9 * vB);
					double vC = 1 / (1 + Math.exp(-uC));

					// finds partial derivatives for u and v values
					double partialWithVc = vC - y;
					double partialWithUc = partialWithVc * vC * (1.0 - vC);

					// finds partial derivatives for u and v values
					double partialWithVa = w8 * partialWithUc;
					double partialVaOverPartialUa;

					if (uA >= 0)
						partialVaOverPartialUa = 1;
					else
						partialVaOverPartialUa = 0;

					double partialWithUa = partialWithVa * 
							partialVaOverPartialUa;

					// finds partial derivatives for u and v values
					double partialWithVb = w9 * partialWithUc;
					double partialVbOverPartialUb;

					if (uB >= 0)
						partialVbOverPartialUb = 1;
					else
						partialVbOverPartialUb = 0;

					double partialWithUb = partialWithVb * 
							partialVbOverPartialUb;

					// finds partial derivatives edge weights
					double derivativeWithWeight1 = 1 * partialWithUa;
					double derivativeWithWeight2 = x1 * partialWithUa;
					double derivativeWithWeight3 = x2 * partialWithUa;
					double derivativeWithWeight4 = 1 * partialWithUb;
					double derivativeWithWeight5 = x1 * partialWithUb;
					double derivativeWithWeight6 = x2 * partialWithUb;
					double derivativeWithWeight7 = 1 * partialWithUc;
					double derivativeWithWeight8 = vA * partialWithUc;
					double derivativeWithWeight9 = vB * partialWithUc;
					
					// updates edge weights
					w1 = w1 - (n * derivativeWithWeight1);
					w2 = w2 - (n * derivativeWithWeight2);
					w3 = w3 - (n * derivativeWithWeight3);
					w4 = w4 - (n * derivativeWithWeight4);
					w5 = w5 - (n * derivativeWithWeight5);
					w6 = w6 - (n * derivativeWithWeight6);
					w7 = w7 - (n * derivativeWithWeight7);
					w8 = w8 - (n * derivativeWithWeight8);
					w9 = w9 - (n * derivativeWithWeight9);

					// reads eval files
					BufferedReader bu = new BufferedReader(new FileReader
							("hw2_midterm_A_eval.txt"));
					for (String evalLine; (evalLine = bu.readLine()) != null;)
					{
						String[] evalData = evalLine.split("\\s+");

						// updates x1,x2, and y foe eval.txt
						Double x1E = Double.parseDouble(evalData[0]);
						Double x2E = Double.parseDouble(evalData[1]);
						Double yE = Double.parseDouble(evalData[2]);

						// pdates new u and v values
						double newUa = w1 + (w2 * x1E) + (w3 * x2E);
						double newVa = max(newUa, 0);

						double newUb = w4 + (w5 * x1E) + (w6 * x2E);
						double newVb = max(newUb, 0);

						double newUc = w7 + (w8 * newVa) + (w9 * newVb);
						double newVc = 1 / (1 + Math.exp(-newUc));

						// increases error
						error += (0.5) * Math.pow(newVc - yE, 2);

					}
					bu.close();
    
					
					// prints updates weights
					System.out.println(String.format("%.5f", x1) + " " + 
							String.format("%.5f", x2) + " "
							+ String.format("%.5f", y));

					System.out.print(String.format("%.5f", w1) + " " +
							String.format("%.5f", w2) + " "
							+ String.format("%.5f", w3) + " ");
					System.out.print(String.format("%.5f", w4) + " " + 
							String.format("%.5f", w5) + " "
							+ String.format("%.5f", w6) + " ");
					System.out.println(String.format("%.5f", w7) + " " + 
							String.format("%.5f", w8) + " "
							+ String.format("%.5f", w9));
					
					// prints the evaluation set error under the updated w
					System.out.println(String.format("%.5f", error));

				}

			} catch (FileNotFoundException e) {
				e.printStackTrace();
			} catch (IOException e) {
				e.printStackTrace();
			}
		}

		// run T epochs. At the end of each epoch, print w, then on a separate
		// line the evaluation set error. (repeats same steps as in flag == 600
		// T times for more epochs based on cmd arg
		if (flag == 700) {

			// updates step size and T
			double n = Double.valueOf(args[10]);
			int times = Integer.valueOf(args[11]);
			double error = 0;

			// runs T times for T epochs
			for (int i = 0; i < times; i++) {
				
				// reads train.txt files
				try (BufferedReader br = new BufferedReader(new FileReader
						("hw2_midterm_A_train.txt"))) {

					for (String line; (line = br.readLine()) != null;) {
						error = 0;
						String[] data = line.split("\\s+");

						// updates x1, x2 and y values
						Double x1 = Double.parseDouble(data[0]);
						Double x2 = Double.parseDouble(data[1]);
						Double y = Double.parseDouble(data[2]);

						// finds u and v values for node A
						double uA = w1 + (w2 * x1) + (w3 * x2);
						double vA = max(uA, 0);

						// finds u and v values for node B
						double uB = w4 + (w5 * x1) + (w6 * x2);
						double vB = max(uB, 0);

						// finds u and v values for node C
						double uC = w7 + (w8 * vA) + (w9 * vB);
						double vC = 1 / (1 + Math.exp(-uC));

						// finds partial derivatives w.r.t v_C and u_C
						double partialWithVc = vC - y;
						double partialWithUc = partialWithVc * vC * (1.0 - vC);

						// finds partial derivatives w.r.t v_A and u_A
						double partialWithVa = w8 * partialWithUc;
						double partialVaOverPartialUa;

						if (uA >= 0)
							partialVaOverPartialUa = 1;
						else
							partialVaOverPartialUa = 0;

						double partialWithUa = partialWithVa * 
								partialVaOverPartialUa;

						// finds partial derivatives w.r.t v_B and u_B
						double partialWithVb = w9 * partialWithUc;
						double partialVbOverPartialUb;

						if (uB >= 0)
							partialVbOverPartialUb = 1;
						else
							partialVbOverPartialUb = 0;

						double partialWithUb = partialWithVb * 
								partialVbOverPartialUb;

						// finds partial derivative w.r.t edge weights
						double derivativeWithWeight1 = 1 * partialWithUa;
						double derivativeWithWeight2 = x1 * partialWithUa;
						double derivativeWithWeight3 = x2 * partialWithUa;
						double derivativeWithWeight4 = 1 * partialWithUb;
						double derivativeWithWeight5 = x1 * partialWithUb;
						double derivativeWithWeight6 = x2 * partialWithUb;
						double derivativeWithWeight7 = 1 * partialWithUc;
						double derivativeWithWeight8 = vA * partialWithUc;
						double derivativeWithWeight9 = vB * partialWithUc;
						
						// updates weights
						w1 = w1 - (n * derivativeWithWeight1);
						w2 = w2 - (n * derivativeWithWeight2);
						w3 = w3 - (n * derivativeWithWeight3);
						w4 = w4 - (n * derivativeWithWeight4);
						w5 = w5 - (n * derivativeWithWeight5);
						w6 = w6 - (n * derivativeWithWeight6);
						w7 = w7 - (n * derivativeWithWeight7);
						w8 = w8 - (n * derivativeWithWeight8);
						w9 = w9 - (n * derivativeWithWeight9);

						
						// reads rval.txt
						BufferedReader bu = new BufferedReader(new FileReader
								("hw2_midterm_A_eval.txt"));
						for (String evalLine; 
								(evalLine = bu.readLine()) != null;) {

							String[] evalData = evalLine.split("\\s+");

							// finds corresponding x1, x2, and y values
							Double x1E = Double.parseDouble(evalData[0]);
							Double x2E = Double.parseDouble(evalData[1]);
							Double yE = Double.parseDouble(evalData[2]);

							// finds corresponding u and v for node A
							double newUa = w1 + (w2 * x1E) + (w3 * x2E);
							double newVa = max(newUa, 0);

							// finds corresponding u and v for node B
							double newUb = w4 + (w5 * x1E) + (w6 * x2E);
							double newVb = max(newUb, 0);

							// finds corresponding u and v for node B
							double newUc = w7 + (w8 * newVa) + (w9 * newVb);
							double newVc = 1 / (1 + Math.exp(-newUc));

							
							// updates error
							error += (0.5) * Math.pow(newVc - yE, 2);

						}
						bu.close();

					}

				} catch (FileNotFoundException e) {
					e.printStackTrace();
				} catch (IOException e) {
					e.printStackTrace();
				}
  
				// prints updated weigts for every epoch
				System.out.print(String.format("%.5f", w1) + " " +
				String.format("%.5f", w2) + " "
						+ String.format("%.5f", w3) + " ");
				System.out.print(String.format("%.5f", w4) + " " + 
						String.format("%.5f", w5) + " "
						+ String.format("%.5f", w6) + " ");
				System.out.println(
						String.format("%.5f", w7) + " " + 
				String.format("%.5f", w8) + " " + String.format("%.5f", w9));
				
				// prints error for each epoch
				System.out.println(String.format("%.5f", error));
			}
		}

		// FLAG=800 has the same input as FLAG=700. But we will stop as soon 
		// as evaluation set error starts to increase after completing a whole
		// epoch. Then computes the test set classification accuracy
		if (flag == 800) {
			
			// initializes step size and T
			double n = Double.valueOf(args[10]);
			int times = Integer.valueOf(args[11]);
						
			double error = 0;
			int epochNum = 0;
			double errorTemp = 0;

			// runs T times for T epochs
			for (int i = 0; i < times; i++) {
				
				// reads train.txt
				try (BufferedReader br = new BufferedReader
						(new FileReader("hw2_midterm_A_train.txt"))) {

					for (String line; (line = br.readLine()) != null;) {
						error = 0;
						String[] data = line.split("\\s+");

						// updates x1, x2 and y values for each student
						Double x1 = Double.parseDouble(data[0]);
						Double x2 = Double.parseDouble(data[1]);
						Double y = Double.parseDouble(data[2]);

						
						double uA = w1 + (w2 * x1) + (w3 * x2);
						double vA = max(uA, 0);

						double uB = w4 + (w5 * x1) + (w6 * x2);
						double vB = max(uB, 0);

						double uC = w7 + (w8 * vA) + (w9 * vB);
						double vC = 1 / (1 + Math.exp(-uC));

						double partialWithVc = vC - y;
						double partialWithUc = partialWithVc * vC * (1.0 - vC);
 
						double partialWithVa = w8 * partialWithUc;
						double partialVaOverPartialUa;

						if (uA >= 0)
							partialVaOverPartialUa = 1;
						else
							partialVaOverPartialUa = 0;

						double partialWithUa = partialWithVa * 
								partialVaOverPartialUa;

						double partialWithVb = w9 * partialWithUc;
						double partialVbOverPartialUb;

						if (uB >= 0)
							partialVbOverPartialUb = 1;
						else
							partialVbOverPartialUb = 0;

						double partialWithUb = partialWithVb * 
								partialVbOverPartialUb;

						double derivativeWithWeight1 = 1 * partialWithUa;
						double derivativeWithWeight2 = x1 * partialWithUa;
						double derivativeWithWeight3 = x2 * partialWithUa;
						double derivativeWithWeight4 = 1 * partialWithUb;
						double derivativeWithWeight5 = x1 * partialWithUb;
						double derivativeWithWeight6 = x2 * partialWithUb;
						double derivativeWithWeight7 = 1 * partialWithUc;
						double derivativeWithWeight8 = vA * partialWithUc;
						double derivativeWithWeight9 = vB * partialWithUc;
						
						
						w1 = w1 - (n * derivativeWithWeight1);
						w2 = w2 - (n * derivativeWithWeight2);
						w3 = w3 - (n * derivativeWithWeight3);
						w4 = w4 - (n * derivativeWithWeight4);
						w5 = w5 - (n * derivativeWithWeight5);
						w6 = w6 - (n * derivativeWithWeight6);
						w7 = w7 - (n * derivativeWithWeight7);
						w8 = w8 - (n * derivativeWithWeight8);
						w9 = w9 - (n * derivativeWithWeight9);

						BufferedReader bu = new BufferedReader
								(new FileReader("hw2_midterm_A_eval.txt"));
						for (String evalLine; 
								(evalLine = bu.readLine()) != null;) {
							// System.out.println(line);
							String[] evalData = evalLine.split("\\s+");

							Double x1E = Double.parseDouble(evalData[0]);
							Double x2E = Double.parseDouble(evalData[1]);
							Double yE = Double.parseDouble(evalData[2]);

							double newUa = w1 + (w2 * x1E) + (w3 * x2E);
							double newVa = max(newUa, 0);

							double newUb = w4 + (w5 * x1E) + (w6 * x2E);
							double newVb = max(newUb, 0);

							double newUc = w7 + (w8 * newVa) + (w9 * newVb);
							double newVc = 1 / (1 + Math.exp(-newUc));

							error += (0.5) * Math.pow(newVc - yE, 2);

						}
						bu.close();

					}

				} catch (FileNotFoundException e) {
					e.printStackTrace();
				} catch (IOException e) {
					e.printStackTrace();
				}

				epochNum++;

				// will stop as soon as evaluation set error starts
				// to increase after completing a whole epoch
				if (error > errorTemp && epochNum > 1)
					break;

				errorTemp = error;

			}

			System.out.println(epochNum);

			// prints last weights
			System.out.print(String.format("%.5f", w1) + " " + 
			String.format("%.5f", w2) + " "
					+ String.format("%.5f", w3) + " ");
			System.out.print(String.format("%.5f", w4) + " " +
					String.format("%.5f", w5) + " "
					+ String.format("%.5f", w6) + " ");
			System.out.println(
					String.format("%.5f", w7) + " " + 
			String.format("%.5f", w8) + " " + String.format("%.5f", w9));
			
			// prints corresponding errors
			System.out.println(String.format("%.5f", error));

			double correct = 0;

			// uses trained neural to check accouracy for test files
			BufferedReader bu;
			try {
				bu = new BufferedReader(new FileReader
						("hw2_midterm_A_test.txt"));
				try {
					for (String testLine; (testLine = bu.readLine()) != null;)
					{
						// System.out.println(line);
						String[] testData = testLine.split("\\s+");

						Double x1T = Double.parseDouble(testData[0]);
						Double x2T = Double.parseDouble(testData[1]);
						Double yT = Double.parseDouble(testData[2]);

						double newUa = w1 + (w2 * x1T) + (w3 * x2T);
						double newVa = max(newUa, 0);

						double newUb = w4 + (w5 * x1T) + (w6 * x2T);
						double newVb = max(newUb, 0);

						double newUc = w7 + (w8 * newVa) + (w9 * newVb);
						double newVc = 1 / (1 + Math.exp(-newUc));

						// prediction is similar to actual y values then
						// increase #correct
						if ((newVc >= 0.5 && yT == 1) || 
								(newVc < 0.5 && yT == 0)) {
							correct++;
						}

					}
				} catch (NumberFormatException e) {
					e.printStackTrace();
				} catch (IOException e) {
					e.printStackTrace();
				}
			} catch (FileNotFoundException e) {
				e.printStackTrace();
			}

			// prints accuracy
			// #correct/total set
			System.out.println(String.format("%.5f", correct / 25));

		}

	}

	/**
	 * method to find which double value is bigger
	 * 
	 * @param j double term to be compared
	 * @param i double term to be compared
	 * @return bigger term between i and j
	 */
	private static double max(double j, double i) {

		if (j >= i)
			return j;

		else
			return i;
	}
}
