/**
 * This assignment is to find all the genes in a DNA string.
 * Algorithm to identify multiple genes in a strand of DNA
 * To find the first gene, find the start codon ATG.
 * Next look immediately past ATG for the first occurrence of each of the three stop codons TAG, TGA, and TAA.
 * If the length of the substring between ATG and any of these three stop codons is a multiple of three, then a candidate for a gene is the start codon through the end of the stop codon.
 * If there is more than one valid candidate, the smallest such string is the gene. The gene includes the start and stop codon.
 * If no start codon was found, then you are done.
 * If a start codon was found, but no gene was found, then start searching for another gene via the next occurrence of a start codon starting immediately after the start codon that didn't yield a gene.
 * If a gene was found, then start searching for the next gene immediately after this found gene.
 * Note that according to this algorithm, for the string "ATGCTGACCTGATAG", ATGCTGACCTGATAG could be a gene, but ATGCTGACCTGA would not be, even though it is shorter, because another instance of 'TGA' is found first that is not a multiple of three away from the start codon.

 * @author Tianjia Chen
 */

import edu.duke.*;
import java.io.*;

public class multiplegene {
    public int findStartIndex(String dna, int Index) {
        dna = dna.toLowerCase();
        int start = dna.indexOf("atg", Index);
        if (start != -1) return start;
        else return -1;
    }

    public int findStopIndex(String dna, int Index) {
        dna = dna.toLowerCase();
        int n = dna.length();
        
        int stop1 = dna.indexOf("taa", Index+3);
        System.out.println(stop1);
        if (stop1 == -1 || (stop1-Index)%3 != 0) stop1 = n+1;
        int stop2 = dna.indexOf("tag", Index+3);
        if (stop2 == -1 || (stop2-Index)%3 != 0) stop2 = n+1;
        int stop3 = dna.indexOf("tga", Index+3);
        if (stop3 == -1 || (stop3-Index)%3 != 0) stop3 = n+1;
    
        int stop = Math.min(stop1, Math.min(stop2, stop3));
        System.out.println(stop);
        if (stop == n+1) return -1;
        else return stop;
    }
    
    public void printAll(String dna) {
        String dna_original = dna;
        int n = dna.length();
        int index = 0;
        while(true) {
            int start = findStartIndex(dna, index);
            System.out.println(start);
            if (start == -1 | index >= n) {
                break;
            }
            int stop = findStopIndex(dna, start);
            if (stop == -1) index = start+3;
            else { 
                System.out.println(stop);
                System.out.println(dna_original.substring(start, stop+3));
                index = stop +3;
             
            }
        }
    }
    
    public void testFinder() {
        String dna = "CATGTAATAGATGAATGACTGATAGATATGCTTGTATGCTATGAAAATGTGAAATGACCCA";
        printAll(dna);
    }
}

