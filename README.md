# Computer-Organization-and-Design-Lab4


`timescale 1ns / 1ps

module All_States(
    input x,
    input clk,
    input rst,
    output reg s,
    output reg v
    );
    parameter S0 = 3'b000,
              S1 = 3'b010,
              S2 = 3'b001,
              S3 = 3'b101,
              S4 = 3'b011,
              S5 = 3'b100,
              S6 = 3'b111;

reg [2:0] state;



    always@(negedgeclk)
    begin
        case (state)
            S0: begin
                v <= 0;
                if (x == 0)begin
                    state <= S1;
                    s <= 1;
                    end
                else begin
                    state <= S2;
                    s <= 0;
                    end
            end
            S1: begin
                v <= 0;
if(x == 0)begin
                    state <= S3;
                    s <= 1;
                    end
                else begin
                    state <= S4;
                    s <= 0;
                    end
            end
            S2: begin
                state <= S4;
                v <= 0;
                if (x == 0)
                    s <= 0;
                else
                    s <= 1;
            end
            S3: begin
                state <= S5;
                v <= 0;
                if (x == 0)
                    s <= 0;
                else
                    s <= 1;
            end
            S4: begin
                v <= 0;
                if (x ==0)begin
                    state <= S5;
                    s <= 1;
                    end
                else begin
                    state <= S6;
                    s <= 0;
                    end
            end
            S5: begin
                state <= S0;
                v <= 0;
                if (x==0)
                    s <= 0;
                else
                    s <= 1;
            end
            S6: begin
                state <= S0;
                if (x==0)begin
                    s <= 1;
                    v <= 0;
                    end
                else begin
                    s <= 0;
                    v <= 1;
                    end
            end
default :state<= S0;
endcase
    end            
endmodule
