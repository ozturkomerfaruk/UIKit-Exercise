```swift
import UIKit

class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .yellow

        let button = UIButton(type: .system)
        button.setTitle("Open Red VC", for: .normal)
        button.addTarget(self, action: #selector(openRedVC), for: .touchUpInside)

        button.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(button)
        NSLayoutConstraint.activate([
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            button.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }

    @objc private func openRedVC() {
        let redVC = RedViewController()
        if let sheet = redVC.sheetPresentationController {
            sheet.detents = [.medium(), .large()] // Yarım ve tam ekran seçenekleri
            sheet.prefersGrabberVisible = true // Çekme çubuğunu göster
        }
        present(redVC, animated: true)
    }
}

class RedViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .red

        let button = UIButton(type: .system)
        button.setTitle("Dismiss", for: .normal)
        button.addTarget(self, action: #selector(dismissVC), for: .touchUpInside)

        button.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(button)
        NSLayoutConstraint.activate([
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            button.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }

    @objc private func dismissVC() {
        dismiss(animated: true)
    }
}
```
