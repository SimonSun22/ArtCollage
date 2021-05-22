/*************************************************************************
 *  Compilation:  javac ArtCollage.java
 *  Execution:    java ArtCollage
 *
 *  @author: Denghao Sun email: ds1665@scarletmail.rutgers.edu netid: ds1665
 *
 *************************************************************************/

import java.awt.Color;

public class ArtCollage {

    // The orginal picture
    private Picture original;

    // The collage picture
    private Picture collage;

    // The collage Picture consists of collageDimension X collageDimension tiles
    private int collageDimension;

    // A tile consists of tileDimension X tileDimension pixels
    private int tileDimension;
    
    /*
     * One-argument Constructor
     * 1. set default values of collageDimension to 4 and tileDimension to 100
     * 2. initializes original with the filename image
     * 3. initializes collage as a Picture of tileDimension*collageDimension x tileDimension*collageDimension, 
     *    where each pixel is black (see all constructors for the Picture class).
     * 4. update collage to be a scaled version of original (see scaling filter on Week 9 slides)
     *
     * @param filename the image filename
     */
    public ArtCollage (String filename) {

        this.collageDimension = 4;
        this.tileDimension = 100;
        this.original = new Picture(filename);
        this.collage = new Picture(400, 400);
        for (int tcol = 0; tcol < 400; tcol++)
            for (int trow = 0; trow < 400; trow++){
                int scol = tcol * original.width()  / 400;
                int srow = trow * original.height() / 400;
                Color color = original.get(scol, srow);
                collage.set(tcol, trow, color);
            }
    // WRITE YOUR CODE HERE
    }

    /*
     * Three-arguments Constructor
     * 1. set default values of collageDimension to cd and tileDimension to td
     * 2. initializes original with the filename image
     * 3. initializes collage as a Picture of tileDimension*collageDimension x tileDimension*collageDimension, 
     *    where each pixel is black (see all constructors for the Picture class).
     * 4. update collage to be a scaled version of original (see scaling filter on Week 9 slides)
     *
     * @param filename the image filename
     */
    public ArtCollage (String filename, int td, int cd) {

        this.collageDimension = cd;
        this.tileDimension = td;
        int a = cd * td;
        this.original = new Picture(filename);
        this.collage = new Picture(a,a);
        for (int tcol = 0; tcol < a; tcol++)
            for (int trow = 0; trow < a; trow++) {
                int scol = tcol * original.width()  / a;
                int srow = trow * original.height() / a;
                Color color = original.get(scol, srow);
                collage.set(tcol, trow, color);
            }

    // WRITE YOUR CODE HERE
    }

    /*
     * Returns the collageDimension instance variable
     *
     * @return collageDimension
     */
    public int getCollageDimension() {

        return collageDimension;

    // WRITE YOUR CODE HERE
    }

    /*
     * Returns the tileDimension instance variable
     *
     * @return tileDimension
     */
    public int getTileDimension() {

        return tileDimension;

    // WRITE YOUR CODE HERE
    }

    /*
     * Returns original instance variable
     *
     * @return original
     */
    public Picture getOriginalPicture() {

        return original;

    // WRITE YOUR CODE HERE
    }

    /*
     * Returns collage instance variable
     *
     * @return collage
     */
    public Picture getCollagePicture() {

        return collage;

    // WRITE YOUR CODE HERE
    }
    
    /*
     * Display the original image
     * Assumes that original has been initialized
     */
    public void showOriginalPicture() {

        original.show();

    // WRITE YOUR CODE HERE
    }

    /*
     * Display the collage image
     * Assumes that collage has been initialized
     */
    public void showCollagePicture() {

        collage.show();

    // WRITE YOUR CODE HERE
    }

    /*
     * Replaces the tile at collageCol,collageRow with the image from filename
     * Tile (0,0) is the upper leftmost tile
     *
     * @param filename image to replace tile
     * @param collageCol tile column
     * @param collageRow tile row
     */
    public void replaceTile (String filename,  int collageCol, int collageRow) {

        int a = getTileDimension();
        this.collage = getCollagePicture();
        Picture source = new Picture(filename);
        Picture target = new Picture(a,a);
        for (int tcol = 0; tcol < a; tcol++)
            for (int trow = 0; trow < a; trow++) {
                int scol = tcol * source.width()  / a;
                int srow = trow * source.height() / a;
                Color color = source.get(scol, srow);
                target.set(tcol, trow, color);
            }
        
        for (int col = 0; col < a; col++) {
            for (int row = 0; row < a; row++) {
                Color color = target.get(col, row);
                collage.set((collageCol*a)+col, (collageRow*a)
                    +row, color);
            }
        }
        collage.show();

    // WRITE YOUR CODE HERE
    }
    
    /*
     * Makes a collage of tiles from original Picture
     * original will have collageDimension x collageDimension tiles, each tile
     * has tileDimension X tileDimension pixels
     */
    public void makeCollage () {

        int width = getTileDimension();
        int size = getCollageDimension();
        int a = width*size;
        this.collage = new Picture(a,a);
        Picture ori = getOriginalPicture();
        
        for (int col = 0; col < width; col++) {
            for (int row = 0; row < width; row++) {
                int scol = col * ori.width()  / width;
                int srow = row * ori.height() / width;
                Color color = ori.get(scol, srow);
                for (int i = 0; i < size; i++) {
                    for (int j = 0; j < size; j++) {
                        collage.set(width*j + col, width*i + row, color);
                    }
                }
            }
        }
        collage.show();

    // WRITE YOUR CODE HERE
    }

    /*
     * Colorizes the tile at (collageCol, collageRow) with component 
     * (see Week 9 slides, the code for color separation is at the 
     *  book's website)
     *
     * @param component is either red, blue or green
     * @param collageCol tile column
     * @param collageRow tile row
     */
    public void colorizeTile (String component,  int collageCol, int collageRow) {

        String r = "red";
        String b = "blue";
        String g = "green";
        int width = getTileDimension();
        this.collage = getCollagePicture();

        for (int col = 0; col < width; col++) {
            for (int row = 0; row < width; row++) {
                Color color = collage.get((collageCol*width)+col, (collageRow*width)
                    +row);
                if (component.equals(r)) {
                    int newR = color.getRed();
                    collage.set((collageCol*width)+col, (collageRow*width)
                    +row, new Color (newR, 0, 0));
                } else if (component.equals(b)) {
                    int newB = color.getBlue();
                    collage.set((collageCol*width)+col, (collageRow*width)
                    +row, new Color (0, 0, newB));
                } else {
                    int newG = color.getGreen();
                    collage.set((collageCol*width)+col, (collageRow*width)
                    +row, new Color (0, newG, 0));
                }
            }
        }
        collage.show();

    // WRITE YOUR CODE HERE
    }

    /*
     * Greyscale tile at (collageCol, collageRow)
     * (see Week 9 slides, the code for luminance is at the book's website)
     *
     * @param collageCol tile column
     * @param collageRow tile row
     */

    public void greyscaleTile (int collageCol, int collageRow) {

        int width = getTileDimension();
        this.collage = getCollagePicture();


        for (int col = 0; col < width; col++) {
            for (int row = 0; row < width; row++) {
                Color color = collage.get((collageCol*width)+col, (collageRow*width)
                    +row);
                Color gray = Luminance.toGray(color);
                collage.set((collageCol*width)+col, (collageRow*width)
                    +row, gray);
            }
        }
        collage.show();

    // WRITE YOUR CODE HERE
    }


    // Test client 
    public static void main (String[] args) {

        ArtCollage art = new ArtCollage(args[0], 200, 2);
        art.makeCollage();
        art.replaceTile(args[1],0,1);
        art.replaceTile(args[2],1,0);
        art.replaceTile(args[3],1,1);
        art.colorizeTile("green",0,0);
        art.showCollagePicture();

    }
}
