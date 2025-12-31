# Call-of-duty-
Call of duty 
import SwiftUI

struct ContentView: View {
    @State private var espEnabled = false

    var body: some View {
        ZStack {
            Color.black.ignoresSafeArea()

            // زر ESP مربع صغير أسود
            VStack {
                Spacer()
                HStack {
                    Spacer()
                    Button(action: {
                        espEnabled.toggle()
                    }) {
                        Rectangle()
                            .fill(Color.black)
                            .frame(width: 35, height: 35)
                            .overlay(
                                Text("ESP")
                                    .font(.system(size: 10, weight: .bold))
                                    .foregroundColor(.white)
                            )
                            .cornerRadius(6)
                    }
                    .padding(.trailing, 20)
                    .padding(.bottom, 20)
                }
            }

            // ESP Box + Line (وهمي)
            if espEnabled {

                // Box
                Rectangle()
                    .stroke(Color.red, lineWidth: 3)
                    .frame(width: 180, height: 260)
                    .position(x: UIScreen.main.bounds.midX,
                              y: UIScreen.main.bounds.midY - 40)

                // Line من اللاعب (أسفل الشاشة) إلى البوكس
                Path { path in
                    path.move(
                        to: CGPoint(
                            x: UIScreen.main.bounds.midX,
                            y: UIScreen.main.bounds.maxY
                        )
                    )
                    path.addLine(
                        to: CGPoint(
                            x: UIScreen.main.bounds.midX,
                            y: UIScreen.main.bounds.midY - 40
                        )
                    )
                }
                .stroke(Color.green, lineWidth: 2)
            }
        }
    }
}

#Preview {
    ContentView()
}
