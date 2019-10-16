
public class Main
{
    public static void main(String[] args)
    {
        int[][]grid= {
                {5,3,1,5,6,1,0,0,0},
                {6,4,7,2,9,8,0,0,0},
                {2,9,8,3,4,7,0,6,0},
                {8,0,0,0,6,0,0,0,3},
                {4,0,0,8,0,3,0,0,1},
                {7,0,0,0,2,0,0,0,6},
                {0,6,0,0,0,0,2,8,0},
                {0,0,0,4,1,9,0,0,5},
                {0,0,0,0,8,0,0,7,9}
                };

        boolean isRight = true;

        int columnPointer;
        int rowPointer;
        columnPointer = rowPointer = 0;



        int[] tempArr;
        for(int i = 0 ; i < grid.length ; i++)
        {
            if(i%3 == 0 & i != 0)
            {
                rowPointer += 3;
                columnPointer = 0;
            }

            tempArr = new int[9];
            int counter = 0 ;
            for(int row = rowPointer ; row < rowPointer+3; row++)
                for(int col = columnPointer; col < columnPointer+3; col++)
                {
                    tempArr[counter] = grid[row][col];
                    counter++;
                }

            for(int o = 0 ; o < tempArr.length; o++)
                for(int j = o+1; j < tempArr.length; j++)
                    if(tempArr[o] == tempArr[j] & tempArr[j] != 0) isRight = false;


            columnPointer += 3;
        }


        for(int i = 0 ; i < grid.length; i++)
            for(int j = 0 ; j < grid.length; j++)
                for(int o = j+1; o < grid.length; o++)
                {
                    if (grid[i][j] == grid[i][o] & grid[i][o] != 0) isRight = false;
                    if (grid[j][i] == grid[o][i] & grid[o][i] != 0) isRight = false;
                }


        System.out.println(isRight ? "":"Wrong");
    }

}
